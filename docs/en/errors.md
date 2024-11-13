# Warnings list

When the simulator is launched, checks are made on the schematic to be simulated.

- **Blocking warnings**: the simulator stops checking at the first error encountered, and prevents simulation until the error has been resolved.
- **Non-blocking warnings** : the simulator replaces the value of parameters not found or unreadable by default values and authorizes simulation anyway. 

## Blocking warnings

|BLOCKING| |
| -------------- | ------------------------------------------------------------------------------------------------------------- |
|{nb_doublons} objects named {name} are present in the schematic, only one is allowed||
|the {master} component is missing to control the {slave}||
|the {slave} object is incompatible with the {master} object||
|The {name} object that controls steering is not a motor||
|object {name} that controls steering does not exist||
|Erroneous API address: Expected format: %{I,Q}m.c with m[0.5] and c[0.31], example: %I1.12||
|Erroneous API address: Expected format: %{IW, QW}m.c with m[0.5] and c[0.3], example: %IW1.1||
|The parent of the API object does not exist||
|I/O marker unreadable: must start with %||
|Parent {name} does not exist||
|pin {pin} of object {name} is not connected||
|'dropped_object' {name} does not exist||
|'dropped_object' {name} is not an object of the '_physics'family||
|object {label_pression} is not a label_pression||
|object {label_pression} does not exist||
|the key 'controle1' of {name'} is undefined||
|key 'controle2' of {name'} is undefined||
|control object {ctrl} missing for {slave}||
|the two objects named {name} must be of type SET and RESET||
|the number of {name} objects must be strictly equal to 2 (SET and RESET)||
|two objects named {name} have incompatible families: {slave} and {master}||
|HMI object {name} is incompatible with object {name}||
|sensor collision identifier {name} doesn't find a match||
|false connection found: invalid arrival/departure folio||
|sending {sending} in folio {folio} not connected||
|object {name} {folio} is not simulatable||
|the schema to be simulated is too large||
|serious problem for the component: software bug. Please contact support||

## Non-blocking warnings

|{OUT_INTERVAL} | |
| -------------- | --------------------------------------------- |
|'alpha' {OFF_INTERVAL}| (0 <= alpha <= 100), value set to 50%"|
|'hang' {OFF_INTERVAL}| [true,false], value set to false|
|'etat_init' {HORS_INTERVALLE}| [true,false], value set to false|
|'delai' {HORS_INTERVALLE}| (0.1 <= delai <= 30), value set to 1s|
|'mass' {OFF_INTERVAL}| (0.1 <= mass <= 100 kg)|
|'friction' {OFF_INTERVAL}| (0 <= friction <= 100)|
|'port' {OFF_INTERVAL}| (500 <= port <= 1000), value set to 502|
|'adresse_table_echange'| (0 <= adress <= 1990), value set to 400|
|'ID_unite' {OFF_INTERVAL}| (0 <= ID_unite <= 247), value set to 111|
|'gravity' {OFF_INTERVAL}| (0 <= gravity <= 10), set value 0|
|'damping' {HORS_INTERVALLE}| (0 <= damping <= 10), value set to 0|
|'damping' {OFF_INTERVAL}| (0 <= damping <= 10), {VALUE_SET_TO} 0|
|'value' {OFF_INTERVAL}| (1pF <= value <= 10000uF), value set to 100uF|
|'value' {OFF_INTERVAL}| (1e-3 <= value <= 10e6), value set to 100 ohms|
|'value' {OFF_INTERVAL}| (1e-3 <= value <= 10e6), value set to 100 ohms|
|'alpha' {OFF_INTERVAL}| (0 <= alpha <= 100), value set to 50%|
|'pn' {HORS_INTERVALLE}| (10 W <= Pn <= 22 kW), value set to {values['pn']/1000} kW|
|'vn' {OFF_INTERVAL}| (12 <= vn <= 400 V), value set to {values['vn']} V|
|'vfrein' {OFF_INTERVAL}| (12 <= v <= 400), value set to {values['vn']} V|
|'nm' {OFF_INTERVAL}| (700 <= nm <= 3000), value set to {values['nm']} rpm|
|'nm1' {OFF_INTERVAL}| (700 <= nm1 <= 3000), value set to {values['nm1']} rpm|
|'nm2' {OFF_INTERVAL}| (700 <= nm2 <= 3000), value set to {values['nm2']} rpm|
|'cos' {OFF_INTERVAL}| (0.5 <= cos(phi) <= 1), value set to {values['cos']}|
|'yield' {OFF_INTERVAL}| (0.35 <= yield <= 1), value set to {values['yield']}|
|venroulement' {HORS_INTERVALLE}| (24V <= venroulement <= 400V), value set to 230 V|
|'venroulement1' {HORS_INTERVALLE}| (24V <= vcoil1 <= 400V), value set to 230 V|
|'venroulement2' {HORS_INTERVALLE}| (24V <= venroulement2 <= 400V), value set to 230 V|
|vinduit' {OFF_INTERVAL}| (12V <= vinduit <= 320V), value set to 100 V|
|'coupling' {OFF_INTERVAL}| (star or delta), selected coupling: star|
|'coupling1' {OFF_INTERVAL}| (star or delta), selected coupling: star| 
|'coupling2' {HORS_INTERVALLE}| (star or delta), selected coupling: star| 
|Idn' {OFF_INTERVAL}| (10 mA <= Idn <= 10000 mA), value set to 100 mA|
|'retard_diff' {OFF_INTERVAL}| (0 ms<= retard_diff <= 10000 ms), value set to 0 ms|
|'retard_rth' {HORS_INTERVALLE}| (1s<= retard_rth <= 30s ), value set to 10 s|
|'retard' {HORS_INTERVALLE}| (0 ms<= retard <= 10000 ms), value set to 0ms
|'retard_rth' {HORS_INTERVALLE}| (1s<= retard_rth <= 30s ), value set to 10 s|
|'retard' {OFF_INTERVAL}| (0 ms<= retard <= 10000 ms), value set to 0 ms|
|'Ith' {OFF_INTERVAL}| (0.1 A<= Ith <= 100 A), value set to 10 A|
|'In' {OFF_INTERVAL}| (0.5 A<= In <= 100 A), value set to 10 A|
|'curve' {OFF_INTERVAL}| (B, C or D), value set to C|
|'typeF' {OFF_INTERVAL}| (gG or aM), type selected: aM| 
|'Pn' {OFF_INTERVAL}| (0.5 VA <= Pn <= 200 VA), value set to {values['pn']} W|
|'vn' {OFF_INTERVAL}| (12 <= vn <= 400), value set to {values['vn']} V|
|'Pn' {OFF_INTERVAL}| (0.5 W <= Pn <= 2 kW), value set to {values['pn']} W|
|'color' {OFF_INTERVAL}| (red, green, blue, orange, white), value set to 'red'| (red)
|'tone' {OFF_INTERVAL}| (0.5s <= tone <= 30s), value set to 1s|
|'toff' {OFF_INTERVAL}| (0.5s <= toff <= 30s), value set to 1s|
|'output_range' {OFF_INTERVAL}| min value = (0, 4) and max value = 20, value set to (4,20) mA|
|'output_range' {OFF_INTERVAL}| min value = -30 and max value = 30, value set to (0.10) V|
|'output_scale' {OFF_INTERVAL}| min value = -32768 and max value = 32767, value set to (0.1000)|
|'input_scale' {OFF_INTERVAL}| min value = -32768 and max value = 32767, value set to (0,1000)|
|'voltage_range' {OFF_INTERVAL}| min value = -1000 and max value = 1000, value set to (0.10) V|
|'current_range' {OFF_INTERVAL}| (min,max) = (-1, 1) A, value set to (4,20) mA|
|'pressure' {OFF_INTERVAL}| (0 <= pressure <= 10.0 bar), value set to 6 bar|
|'ve' {OFF_INTERVAL}| (5 <= ve <= 400), value set to {values['vin']} V|
|'vs' {OFF_INTERVAL}| (5 <= vs <= 400), value set to {values['vout']} V|
|'vs1' {OFF_INTERVAL}| (5 <= vs1 <= 400), value set to {values['vout1']} V|
|'vs2' {OFF_INTERVAL}| (5 <= vs2 <= 400), value set to {values['vout2']} V|
|'vbat' {OFF_INTERVAL}| (0 <= vbat <= 400), value set to {values['vbat']} V|
|{power} {OFF_INTERVAL}| (90 W <= {power} <= 22 kW), value set to {values[{power}]/1000} kW|


|UNREADABLE ||
| -------------- | --------------------------------------------- |
|'masse' {UNREADABLE}| value set to 1 kg|
|'friction' {UNREADABLE}| value set to 1 |
| 'ip_address' {UNREADABLE}| value set to 127.0.0.1|
| 'port' {UNREADABLE}| value set to 502|
|'adresse_table_echange' {UNREADABLE}| value set to 400|
|'ID_unite' {UNREADABLE}| value set to 111|
|'gravity' {UNREADABLE}| value set to 0|
|'damping' {UNREADABLE}| value set to 0|
|'damping' {UNREADABLE}| {VALUE_SET_TO} 0|
|'value' {UNREADABLE}| value set to 100 uF|
|'value' {UNREADABLE}| value set to 100 ohms|
|'value' {UNREADABLE}| value set to 100 ohms|
|'alpha' {UNREADABLE}| value set to 50%|
|'Pn' {UNREADABLE}| value set to {values['pn']/1000} kW|
|'vn' {UNREADABLE}| value set to {values['vn']} V|
|'v' {UNREADABLE}| value set to {values['vn']} V|
|'nm' {UNREADABLE}| value set to {values['nm']} rpm|
|'nm1' {UNREADABLE}| value set to {values['nm1']} rpm|
|'nm2' {UNREADABLE}| value set to {values['nm2']} rpm|
|'cos' {UNREADABLE}| value set to {values['cos']}|
|'rendement' {UNREADABLE}| value set to {values['rendement']}|
| 'venroulement' {UNREADABLE}| value set to {values['venroulement']/0.98:2.0f} V|
| 'venroulement1' {UNREADABLE}| value set to {values['venroulement1']/0.98:2.0f} V|
|'venroulement2' {UNREADABLE}| value set to {values['venroulement2']/0.98:2.0f} V|
|'vinduit' {UNREADABLE}| value set to {values['va']/0.98:2.0f} V|
|'Idn' {UNREADABLE}| value set to {values['idn']} mA|
|'retard_diff' {UNREADABLE}| {VALUE_SET_TO} {values['retard_diff']} ms|
|'retard_rth' {UNREADABLE}| value set to {values['retard_rth']} s|
|'retard' {UNREADABLE}| value set to {values['retard']} ms|
| 'Ith' {UNREADABLE}| {VALUE_SET_TO} {values['ith']} A|
| 'In' {UNREADABLE}| value set to {values['in']} A|
| 'pn' {UNREADABLE}| value set to {values['pn']} W|
| 'vn' {UNREADABLE}| value set to {values['vn']} V|
|'color' {UNREADABLE}| value set to 'red'|
| 'vn' {UNREADABLE}| value set to 24 V|
|'ton' {UNREADABLE}| value set to 1s|
|'toff' {UNREADABLE}| value set to 1s|
|output_type' {UNREADABLE}| (output_type = V or I), 'output_type' set to 'V'|
|'output_type' {UNREADABLE}| (output_type = V or I), 'output_type' set to 'V'|
|'output_range' {UNREADABLE}| value set to (4.20) mA|
|'output_range' {UNREADABLE}| value set to (0.10) V|
|'output_scale' {UNREADABLE}| value set to (0,1000)|
|input_type' {UNREADABLE}| (input_type = V or I), 'input_type' set to 'V'|
|'input_type' {UNREADABLE}| (input_type = V or I), 'input_type' set to 'V'|
|'input_range' {UNREADABLE}| value set to (4.20) mA|
|'input_range' {UNREADABLE}| value set to (0.10) V|
|'input_scale' {UNREADABLE}| value set to (0,1000)|
|'voltage_range' {UNREADABLE}| value set to (0,10) V|
|'current_range' {UNREADABLE}| value set to (4.20) mA|
|'pressure' {UNREADABLE}| value set to {values['pressure']} bar|
|'ve' {UNREADABLE}| value set to {values['vin']} V|
| 'vs' {UNREADABLE}| value set to {values['vout']} V|
| 'vs1' {UNREADABLE}| value set to {values['vout1']} V|
| 'vs2' {UNREADABLE}| value set to {values['vout2']} V|
| 'vbat' {UNREADABLE}| value set to {values['vbat']} V|
|'format' {UNREADABLE}| (format = ac or dc), 'format' set to 'dc'|
|{power} {UNREADABLE}| value set to {values[{power}]/1000} kW|
|parameter {k} {UNREADABLE}| factory value {values[k]} {limits[k][0]} selected|