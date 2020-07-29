Maintenant que ta BDD est prête, tu vas répondre aux questions ci-dessous :

a) Niveau facile

Quel est le nombre total d'objets Album contenus dans la base (sans regarder les id bien sûr) ? : 
Album.count : 347

Qui est l'auteur de la chanson "White Room" ?
Track.find_by(title: "White Room") : Eric Clapton

Quelle chanson dure exactement 188133 milliseconds ? 
Track.find_by(duration: 188133) : "Perfect" d'Alanis Morissette

Quel groupe a sorti l'album "Use Your Illusion II" ? 
Album.find_by(title: "Use Your Illusion II").artist : Guns N' Roses

b) Niveau Moyen

Combien y a t'il d'albums dont le titre contient "Great" ? (indice) 13
Album.where("title LIKE '%Great%'").count 

Supprime tous les albums dont le nom contient "music".
Album.where("title like?", "%Music%").destroy_all

Combien y a t'il d'albums écrits par AC/DC ?
Album.where(artist: "AC/DC").count : 2

Combien de chanson durent exactement 158589 millisecondes ?
Track.find_by(duration: 158589).count : 0


c) Niveau Difficile

Pour ces questions, tu vas devoir effectuer des boucles dans la console Rails. C'est peu commun mais c'est faisable, tout comme dans IRB.

puts en console tous les titres de AC/DC.

Track.where(artist: "AC/DC").each do |track|
puts "#{track.title}"
end

puts en console tous les titres de l'album "Let There Be Rock".

Track.where(album: "Let There Be Rock").each do |track|
puts "#{track.title}"
end


Calcule le prix total de cet album ainsi que sa durée totale.

total_price = 0
total_duration = 0
 my_album.each do |track|
  total_price = total_price + track.price
  total_duration = total_duration + track.duration
 end

Prix total : 7.920000000000001
Durée totale : 2453259 millisecondes

Calcule le coût de l'intégralité de la discographie de "Deep Purple".

total_price = 0
Track.where(artist: "Deep Purple").each do |track|
 total_price = total_price + track.price
end
total_price = 90.0899999999999

Modifie (via une boucle) tous les titres de "Eric Clapton" afin qu'ils soient affichés avec "Britney Spears" en artist.

Track.where(artist: "Eric Clapton").each do |track|
 track.update(artist: "Britney Spears")
end

