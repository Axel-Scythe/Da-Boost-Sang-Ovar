# Da-Boost-Sang-Ovar

//		javascript code
//		script_name: randMeasure.js
//
//		author: Bent Electrode
//		description: The measures are rng'd.
//

init();

var tempo = (Math.random()*141)+80;
if(tempo > 195){
  tempo = 195;
}
setTempo(Math.floor(tempo));


//numbers
var index;

//sounds
var air = Y26_ALERT_1;
var guitar = [RD_ROCK_POPRHYTHM_GUITAR_1,RD_ROCK_POPRHYTHM_GUITAR_2,RD_ROCK_POPRHYTHM_GUITAR_3,RD_ROCK_POPRHYTHM_GUITAR_4,RD_ROCK_POPRHYTHM_GUITAR_5,RD_ROCK_POPRHYTHM_GUITAR_6,RD_ROCK_POPRHYTHM_GUITAR_7,RD_ROCK_POPRHYTHM_GUITAR_8,RD_ROCK_POPRHYTHM_GUITAR_9,RD_ROCK_POPRHYTHM_GUITAR_10];

var drums = [ELECTRO_DRUM_MAIN_BEAT_001,ELECTRO_DRUM_MAIN_BEAT_002,ELECTRO_DRUM_MAIN_BEAT_003,ELECTRO_DRUM_MAIN_BEAT_004,ELECTRO_DRUM_MAIN_BEAT_005,ELECTRO_DRUM_MAIN_BEAT_006,ELECTRO_DRUM_MAIN_BEAT_007,ELECTRO_DRUM_MAIN_BEAT_008,ELECTRO_DRUM_MAIN_BEAT_009,ELECTRO_DRUM_MAIN_BEAT_010];

var vox = YG_ELECTRO_VOX_1;


//Beat Strings
var airBeat = ["--0--0+---0-0+-0", "0--0+-00---0-0+0", "0-0-0-0-0-0-0-0-", "0+++0+++0+++0+++", "-----0--0--00--0"];

//Media
for(var measure = 1; measure < 64; measure+=4){
  index = Math.floor(Math.random()*10);
  fitMedia(guitar[index], 1, measure, measure+4);
}

for(var measure = 1; measure < 64; measure+=2){
  index = Math.floor(Math.random()*10);
  fitMedia(drums[index], 2, measure, measure+2);
}

for(var i = 0; i<11; i++){
measure = Math.floor(Math.random()*64) + 1;
var rAirBeat = shuffleString(airBeat[Math.floor(Math.random()*5)]);
makeBeat(air, 3, ((Math.random()*64)+1), rAirBeat);
fitMedia(vox, 4, measure, measure + 1); 
}


//Effects
setEffect(3, VOLUME, GAIN, +12);
setEffect(4, VOLUME, GAIN, +12);
setEffect(1, VOLUME, GAIN, -6);
setEffect(2, VOLUME, GAIN, -6);

setEffect(MASTER_TRACK, VOLUME, GAIN, 0, 60, -60, 65);
finish();
