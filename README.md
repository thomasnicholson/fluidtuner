# fluidtuner
Quick batch generating of Fluidsynth tuning data from any number of 12-note, octave-repeating tunings stored in a simple, human-readable text file.

## Usage

While Fluidtuner itself is a Python program, the actual tuning information to be processed is stored in a separate text file.  Each regular line of this file is a single 12-note, octave-repeating tuning consisting of a comma-separated list of ratios. Ratios may take these forms:

- Any single whole number (e.g. 5)
- Any fraction of whole numbers (e.g. 3/2)
- Any fraction of decimal numbers (e.g. 1.2378/1.1854)
- Any single decimal number (e.g. 1.9875)

Note: Fluidtuner assumes that the order of the ratios on each line is in the order you intended and therefore does not do any sorting. Equally, you should keep in mind that tunings are understood as octave-repeating, so whole and decimal numbers greater or equal to 2 are not useful unless you have an unorthordox usage in mind. This also means that the octave itself should not be included in your tuning information (i.e. do not end a 12-note tuning with 2/1.)

To process the tuning information, run:

    python3 fluidtuner.py /path/to/input/file.txt

An output file (fluidtuner_output.txt by default) is generated containing Fluidsynth tuning data. This data may be pasted into your Fluidsynth configuration file for use in Fluidsynth. 

## Options

Fluidtuner accepts the following options:

    --unity

The chromatic note of the tuning’s unity 1/1 (string, default: C).
Must be one of must be one of C, C#, Db, D, D#, Eb, E, F, F#, Gb, G, G#, Ab, A, A#, Bb, or B. 
*Note: the diatonic note name must be capitalized*

    --offset

An offset ratio for the tuning’s unity with respect to another reference pitch or Kammerton, where the reference pitch = 0 cents and unity = some cent deviation (string, default: 1/1, i.e. unity itself = 0 cents).
   
    --name

The name of your tuning (string, default: MyTuning).
    
    --bank

The Fluidsynth tuning bank (integer, default: 1).
    
    --program

The program number in tuning bank as start point (integer, default: 0).
    
    --output

The filename for generated Fluidsynth tuning data (string, default: fluidtuner_output.txt)