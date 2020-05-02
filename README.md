# README

a) Niveau facile

* Quel est le nombre total d'objets Album contenus dans la base (sans regarder les id bien sûr) ?
```
> Album.all.count
=> 347
```
* Qui est l'auteur de la chanson "White Room" ?
```
> Track.find_by(title:'White Room').artist
=> Eric Clapton
```
* Quelle chanson dure exactement 188133 milliseconds ?
```
> Track.find_by(duration:188133).title
=> Perfect
```
* Quel groupe a sorti l'album "Use Your Illusion II" ?
```
> Album.find_by(title:"Use Your Illusion II").artist 
=> Guns N Roses
```

b) Niveau Moyen

Combien y a t'il d'albums dont le titre contient "Great" ? (indice)
```
> Album.where("title like ?", "%Great%").size
=> 13
```

* Supprime tous les albums dont le nom contient "music".
```
> Album.where("title like ?", "%music%").destroy_all
```

* Combien y a t'il d'albums écrits par AC/DC ?
```
> Album.where(artist: "AC/DC").size
=> 2
```

* Combien de chanson durent exactement 158589 millisecondes ?
```
> Track.where(duration:158589).size
=> 0
```

c) Niveau Difficile

* puts en console tous les titres de AC/DC.
```
> Track.where(artist: "AC/DC").each{ |track| puts track.title}
=>  For Those About To Rock (We Salute You)
	Put The Finger On You
	Lets Get It Up
	Inject The Venom
	Snowballed
	Evil Walks
	C.O.D.
	Breaking The Rules
	Night Of The Long Knives
	Spellbound
	Go Down
	Dog Eat Dog
	Let There Be Rock
	Bad Boy Boogie
	Problem Child
	Overdose
	Hell Aint A Bad Place To Be
	Whole Lotta Rosie
```

* puts en console tous les titres de l'album "Let There Be Rock".
```
> Track.where(album: "Let There Be Rock").each{|track| puts track.title}
=>	Go Down
	Dog Eat Dog
	Let There Be Rock
	Bad Boy Boogie
	Problem Child
	Overdose
	Hell Aint A Bad Place To Be
	Whole Lotta Rosie
```

* Calcule le prix total de cet album ainsi que sa durée totale.
```
> Track.where(album: "Let There Be Rock").sum(:price)
=> 7.920000000000001
> Track.where(album: "Let There Be Rock").sum(:duraction)
=> 2453259 
```

* Calcule le coût de l'intégralité de la discographie de "Deep Purple".
```
> Track.where(artist: "Deep Purple").sum(:price)
=> 90.0899999999999
```

* Modifie (via une boucle) tous les titres de "Eric Clapton" afin qu'ils soient affichés avec "Britney Spears" en artist.
```
> Track.where(artist: "Eric Clapton").each{|track| track.update(artist: "Britney Spears")}
```

