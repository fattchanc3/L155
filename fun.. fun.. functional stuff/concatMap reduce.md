```js
function() {
// 	'use strict';
	var movieLists = [
		{
			name: "New Releases",
			videos: [
				{
					"id": 70111470,
					"title": "Die Bad",
					"boxarts": [
						{ width: 150, height:200, url:"http://cdn-0.nflximg.com/images/2891/DieBad150.jpg" },
						{ width: 200, height:200, url:"http://cdn-0.nflximg.com/images/2891/DieBad200.jpg" }
					],
					"url": "http://api.netflix.com/catalog/titles/movies/70111470",
					"rating": 4.0,
					"bookmark": []
				},
				{
					"id": 654356453,
					"title": "Bat Boys",
					"boxarts": [
						{ width: 200, height:200, url:"http://cdn-0.nflximg.com/images/2891/BatBoys200.jpg" },
						{ width: 140, height:200, url:"http://cdn-0.nflximg.com/images/2891/BatBoys140.jpg" }

					],
					"url": "http://api.netflix.com/catalog/titles/movies/70111470",
					"rating": 5.0,
					"bookmark": [{ id:432534, time:65876586 }]
				}
			]
		},
		{
			name: "Thrillers",
			videos: [
				{
					"id": 65432445,
					"title": "The Cam",
					"boxarts": [
						{ width: 130, height:200, url:"http://cdn-0.nflximg.com/images/2891/TheCam130.jpg" },
						{ width: 200, height:200, url:"http://cdn-0.nflximg.com/images/2891/TheCam200.jpg" }
					],
					"url": "http://api.netflix.com/catalog/titles/movies/70111470",
					"rating": 4.0,
					"bookmark": []
				},
				{
					"id": 675465,
					"title": "Fractured",
					"boxarts": [
						{ width: 200, height:200, url:"http://cdn-0.nflximg.com/images/2891/Fractured200.jpg" },
						{ width: 120, height:200, url:"http://cdn-0.nflximg.com/images/2891/Fractured120.jpg" },
						{ width: 300, height:200, url:"http://cdn-0.nflximg.com/images/2891/Fractured300.jpg" }
					],
					"url": "http://api.netflix.com/catalog/titles/movies/70111470",
					"rating": 5.0,
					"bookmark": [{ id:432534, time:65876586 }]
				}
			]
		}
	];

    
	// [
	//	 {"id": 675465,"title": "Fractured","boxart":"http://cdn-0.nflximg.com/images/2891/Fracture120.jpg" },
	//	 {"id": 65432445,"title": "The Cam","boxart":"http://cdn-0.nflximg.com/images/2891/TheCam130.jpg" },
	//	 {"id": 654356453,"title": "Bat Boys","boxart":"http://cdn-0.nflximg.com/images/2891/BatBoys140.jpg" },
	//	 {"id": 70111470,"title": "Die Bad","boxart":"http://cdn-0.nflximg.com/images/2891/DieBad150.jpg" }
	// ];

	return movieLists.
		concatMap(function(movieList) {
			return movieList.videos.
			concatMap(v1 => v1.boxarts.
			     reduce((a1, v2) => a1.width < v2.width ? a1 : v2).
			     map(v3 => { //debugger;let test = { "id": v1.id, 'title': v1.title, 'boxart': v3.url };console.log(test);
			     return { "id": v1.id, 'title': v1.title, 'boxart': v3.url }; 
			     })
			    ); 
		});

}
```
