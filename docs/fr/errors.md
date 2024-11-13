# Liste Avertissements

Au lancement du simulateur, des vérifications sont faites sur le schéma à simuler.

- **Avertissement bloquant** : le simulateur arrête la vérification à la première erreur rencontrée et empêche la simulation tant que l'erreur n'est pas résolue.
- **Avertissements non bloquants** : le simulateur remplace la valeur des paramètre non trouvés ou illisibles par des valeurs par défaut et autorise quand même la simulation. 

## Avertissements bloquants

|BLOQUANTS|                                              |
| -------------- | ------------------------------------------------------------------------------------------------------------- |
|{nb_doublons} objets  nommés {name} sont présents dans le schéma, un seul est autorisé||
|il manque le composant {master} pour contrôler le {slave}||
|l'objet {slave} est incompatible avec l'objet {master}||
|L'objet {name} qui contrôle la direction n'est pas un moteur||
|L'objet {name} qui pilote la direction n'existe pas||
|adresse API erronnée : Format attendu : %{I,Q}m.c  avec m[0,5] et c[0,31], exemple : %I1.12||
|adresse API erronnée : Format attendu : %{IW, QW}m.c  avec m[0,5] et c[0,3], exemple : %IW1.1||
|Le parent de l'objet API n'existe pas||
|repère d'E/S illisible : il doit commencer par %||
|Le parent {name} n'existe pas||
|la broche {broche} de l'objet {name} n'est pas raccordée||
|'dropped_object' {name} n'existe pas||
|'dropped_object' {name} n'est pas un objet de la famille '_physique'||
|L'objet {label_pression} n'est pas un label_pression||
|L'objet {label_pression}  n'existe pas||
|la clef 'controle1' de {name'} est non définie||
|la clef 'controle2' de {name'} est non définie||
|objet de contrôle {ctrl} manquant pour {slave}||
|les deux objets nommés {name} doivent être du type SET et RESET||
|le nombre d'objets {name} doit être strictement ègal à 2 (SET et RESET)||
|deux objets nommés  {name} ont des familles incompatibles : {slave} et {master}||
|l'objet IHM {name} est incompatible avec l'objet {name}||
|l'identificateur de collision du capteur {name} ne trouve pas de correspondance||
|liaison fausse trouvée : folio arrivée/départ non valide||
|renvoi {renvoi} dans le folio {folio} non connecté||
|l'objet {name} {folio} n'est pas simulable||
|Le schéma à simuler est trop grand||
|problème grave pour le composant : bug logiciel. Merci de contacter le support||

## Avertissements non bloquants

|{HORS_INTERVALLE} |                                              |
| -------------- | --------------------------------------------- |
|'alpha' {HORS_INTERVALLE}| (0 <= alpha <= 100), valeur réglée à 50%"|
|'accrochage' {HORS_INTERVALLE}| [vrai,faux], valeur réglée à faux|
|'etat_init' {HORS_INTERVALLE}| [vrai,faux], valeur réglée à faux|
|'delai' {HORS_INTERVALLE}| (0.1 <= delai <= 30), valeur réglée à 1s|
|masse' {HORS_INTERVALLE}| (0.1 <= masse <= 100 kg)|
|'friction' {HORS_INTERVALLE}| (0 <= friction <= 100)|
|'port' {HORS_INTERVALLE}| (500 <= port <= 1000), valeur réglée à 502|
|'adresse_table_echange'| (0 <= adress <= 1990), valeur réglée 400|
|'ID_unite' {HORS_INTERVALLE}| (0 <= ID_unite <= 247), valeur réglée 111|
|'gravity' {HORS_INTERVALLE}| (0 <= gravity <= 10), valeur réglée 0|
|'amortisement' {HORS_INTERVALLE}| (0 <= damping <= 10), valeur réglée à 0|
|'damping' {HORS_INTERVALLE}| (0 <= damping <= 10), {VALUE_SET_TO} 0|
|'valeur' {HORS_INTERVALLE}| (1pF <= valeur <= 10000uF), valeur réglée à 100uF|
|'valeur' {HORS_INTERVALLE}| (1e-3 <= valeur <= 10e6), valeur réglée à 100 ohms|
|'valeur' {HORS_INTERVALLE}| (1e-3 <= valeur <= 10e6), valeur réglée à 100 ohms|
|'alpha' {HORS_INTERVALLE}| (0 <= alpha <= 100), valeur réglée à 50%|
|'pn' {HORS_INTERVALLE}| (10 W <= Pn <= 22 kW), valeur réglée à {values['pn']/1000} kW|
|'vn' {HORS_INTERVALLE}| (12 <= vn <= 400 V), valeur réglée à {values['vn']} V|
|'vfrein' {HORS_INTERVALLE}| (12 <= v <= 400), valeur réglée à {values['vn']} V|
|'nm' {HORS_INTERVALLE}| (700 <= nm <= 3000), valeur réglée à {values['nm']} rpm|
|'nm1' {HORS_INTERVALLE}| (700 <= nm1 <= 3000), valeur réglée à {values['nm1']} rpm|
|'nm2' {HORS_INTERVALLE}| (700 <= nm2 <= 3000), valeur réglée à {values['nm2']} rpm|
|'cos' {HORS_INTERVALLE}| (0.5 <= cos(phi) <= 1), valeur réglée à {values['cos']}|
|'rendement' {HORS_INTERVALLE}| (0.35 <= rendement <= 1), valeur réglée à {values['rendement']}|
|'venroulement' {HORS_INTERVALLE}| (24V <= venroulement <= 400V), valeur réglée à 230 V|
|'venroulement1' {HORS_INTERVALLE}| (24V <= vcoil1 <= 400V), valeur réglée à 230 V|
|'venroulement2' {HORS_INTERVALLE}| (24V <= venroulement2 <= 400V), valeur réglée  à 230 V|
|'vinduit' {HORS_INTERVALLE}| (12V <= vinduit <= 320V), valeur réglée à 100 V|
|'couplage' {HORS_INTERVALLE}| (étoile ou triangle), couplage choisi : étoile|
|'couplage1' {HORS_INTERVALLE}|  (étoile ou triangle), couplage choisi : étoile| 
|'couplage2' {HORS_INTERVALLE}|  (étoile ou triangle), couplage choisi : étoile| 
|'Idn' {HORS_INTERVALLE}| (10 mA <= Idn <= 10000 mA), valeur réglée à 100 mA|
|'retard_diff'  {HORS_INTERVALLE}| (0 ms<= retard_diff <= 10000 ms), valeur réglée à 0 ms|
|'retard_rth' {HORS_INTERVALLE}| (1s<= retard_rth <= 30s ), valeur réglée à 10 s|
|'retard' {HORS_INTERVALLE}| (0 ms<= retard <= 10000 ms), valeur réglée à 0 ms|
|'Ith' {HORS_INTERVALLE}| (0.1 A<= Ith <= 100 A), valeur réglée à 10 A|
|'In' {HORS_INTERVALLE}| (0.5 A<= In <= 100 A), valeur réglée à 10 A|
|'courbe' {HORS_INTERVALLE}| (B, C ou D), valeur réglée à C|
|'typeF' {HORS_INTERVALLE}| (gG ou aM), type choisi : aM| 
|'Pn' {HORS_INTERVALLE}| (0.5 VA <= Pn <= 200 VA), valeur réglée à {values['pn']} W|
|'vn'  {HORS_INTERVALLE}| (12 <= vn <= 400), valeur réglée à {values['vn']} V|
|'Pn' {HORS_INTERVALLE}| (0.5 W <= Pn <= 2 kW), valeur réglée à {values['pn']} W|
|'couleur' {HORS_INTERVALLE}| (rouge, vert, bleu, orange, blanc), valeur réglée à 'rouge'|
|'ton' {HORS_INTERVALLE}| (0.5s <= ton <= 30s), valeur réglée à 1s|
|'toff' {HORS_INTERVALLE}| (0.5s <= toff <= 30s), valeur réglée à 1s|
|'output_range' {HORS_INTERVALLE}| valeur min = (0, 4) et valeur maxi = 20, valeur réglée à (4,20) mA|
|'output_range' {HORS_INTERVALLE}| valeur min = -30 et valeur maxi = 30, valeur réglée à (0,10) V|
|'output_scale' {HORS_INTERVALLE}| valeur min = -32768 et valeur maxi = 32767, valeur réglée à (0,1000)|
|'input_scale' {HORS_INTERVALLE}| valeur min = -32768 et valeur maxi = 32767, valeur réglée à (0,1000)|
|'voltage_range' {HORS_INTERVALLE}| valeur min = -1000 et valeur maxi = 1000, valeur réglée à (0,10) V|
|'current_range' {HORS_INTERVALLE}| (min,max) = (-1, 1) A, valeur réglée à (4,20) mA|
|'pression' {HORS_INTERVALLE}| (0 <= pression <= 10.0 bar), valeur réglée à 6 bar|
|'ve' {HORS_INTERVALLE}| (5 <= ve  <= 400), valeur réglée à {values['vin']} V|
|'vs' {HORS_INTERVALLE}| (5 <= vs <= 400), valeur réglée à {values['vout']} V|
|'vs1' {HORS_INTERVALLE}| (5 <= vs1 <= 400), valeur réglée à {values['vout1']} V|
|'vs2' {HORS_INTERVALLE}| (5 <= vs2 <= 400), valeur réglée à {values['vout2']} V|
|'vbat' {HORS_INTERVALLE}| (0 <= vbat <= 400), valeur réglée à {values['vbat']} V|
|{power} {HORS_INTERVALLE}| (90 W <= {power} <= 22 kW), valeur réglée à {values[{power}]/1000} kW|


|ILLISIBLE |                                              |
| -------------- | --------------------------------------------- |
|'masse' {ILLISIBLE}| valeur réglée à  1 kg|
|'friction' {ILLISIBLE}| valeur réglée à  1 |
|'adresse_ip' {ILLISIBLE}| valeur réglée à 127.0.0.1|
|'port' {ILLISIBLE}| valeur réglée à 502|
|'adresse_table_echange' {ILLISIBLE}| valeur réglée à 400|
|'ID_unite' {ILLISIBLE}| valeur réglée à 111|
|'gravity' {ILLISIBLE}| valeur réglée à  0|
|'amortisement' {ILLISIBLE}| valeur réglée à  0|
|'damping' {ILLISIBLE}| {VALUE_SET_TO}  0|
|'valeur' {ILLISIBLE}| valeur réglée à 100 uF|
|'valeur' {ILLISIBLE}| valeur réglée à 100 ohms|
|'valeur' {ILLISIBLE}| valeur réglée à 100 ohms|
|'alpha' {ILLISIBLE}| valeur réglée à 50%|
|'Pn' {ILLISIBLE}| valeur réglée à {values['pn']/1000} kW|
|'vn' {ILLISIBLE}| valeur réglée à {values['vn']} V|
|'v' {ILLISIBLE}| valeur réglée à {values['vn']} V|
|'nm' {ILLISIBLE}| valeur réglée à {values['nm']} rpm|
|'nm1' {ILLISIBLE}| valeur réglée à {values['nm1']} rpm|
|'nm2' {ILLISIBLE}| valeur réglée à {values['nm2']} rpm|
|'cos' {ILLISIBLE}| valeur réglée à {values['cos']}|
|'rendement' {ILLISIBLE}| valeur réglée à {values['rendement']}|
|'venroulement'  {ILLISIBLE}| valeur réglée à {values['venroulement']/0.98:2.0f} V|
|'venroulement1' {ILLISIBLE}| valeur réglée à {values['venroulement1']/0.98:2.0f} V|
|'venroulement2'  {ILLISIBLE}| valeur réglée à {values['venroulement2']/0.98:2.0f} V|
|'vinduit' {ILLISIBLE}| valeur réglée à {values['va']/0.98:2.0f} V|
|'Idn' {ILLISIBLE}| valeur réglée à {values['idn']} mA|
|'retard_diff' {ILLISIBLE}| {VALUE_SET_TO} {values['retard_diff']} ms|
|'retard_rth' {ILLISIBLE}| valeur réglée à {values['retard_rth']} s|
|'retard' {ILLISIBLE}| valeur réglée à {values['retard']} ms|
|'Ith' {ILLISIBLE}| {VALUE_SET_TO} {values['ith']} A|
|'In' {ILLISIBLE}| valeur réglée à {values['in']} A|
|'Pn' {ILLISIBLE}| valeur réglée à {values['pn']} W|
|'vn' {ILLISIBLE}| valeur réglée à {values['vn']} V|
|'couleur' {ILLISIBLE}| valeur réglée à 'rouge'|
|'vn' {ILLISIBLE}| valeur réglée à 24 V|
|'ton' {ILLISIBLE}| valeur réglée à 1s|
|'toff' {ILLISIBLE}| valeur réglée à 1s|
|'output_type' {ILLISIBLE}| (output_type = V ou I), 'output_type' réglé sur 'V'|
|'output_type' {ILLISIBLE}| (output_type = V ou I), 'output_type' réglé sur 'V'|
|'output_range' {ILLISIBLE}| valeur réglée à (4,20) mA|
|'output_range' {ILLISIBLE}| valeur réglée à (0,10) V|
|'output_scale' {ILLISIBLE}| valeur réglée à (0,1000)|
|'input_type' {ILLISIBLE}| (input_type = V ou I), 'input_type' réglé sur 'V'|
|'input_type' {ILLISIBLE}| (input_type = V ou I), 'input_type' réglé sur 'V'|
|'input_range' {ILLISIBLE}| valeur réglée à (4,20) mA|
|'input_range' {ILLISIBLE}| valeur réglée à (0,10) V|
|'input_scale' {ILLISIBLE}| valeur réglée à (0,1000)|
|'v' {ILLISIBLE}| valeur réglée à {values['vn']} V|
|'voltage_range' {ILLISIBLE}| valeur réglée à (0,10) V|
|'current_range' {ILLISIBLE}| valeur réglée à (4,20) mA|
|'pression' {ILLISIBLE}| valeur réglée à {values['pression']} bar|
|'ve' {ILLISIBLE}| valeur réglée à {values['vin']} V|
|'vs' {ILLISIBLE}| valeur réglée à {values['vout']} V|
|'vs1' {ILLISIBLE}| valeur réglée à {values['vout1']} V|
|'vs2' {ILLISIBLE}| valeur réglée à {values['vout2']} V|
|'vbat' {ILLISIBLE}| valeur réglée à {values['vbat']} V|
|'format' {ILLISIBLE}| (format = ac ou dc), 'format' réglé sur 'dc'|
|{power} {ILLISIBLE}| valeur réglée à {values[{power}]/1000} kW|
|paramètre {k} {ILLISIBLE}| valeur d'usine {values[k]} {limits[k][0]} choisie|