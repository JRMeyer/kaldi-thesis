Thesis: Automatic speech recognition using Kaldi
================================================
This repository contains the source code of the thesis and its presentation.
If you want to read the thesis please chose the most recent version in [text/tags/](text/tags) directory. 
Please, use open the pdf file with highest NUMBER suffix to read the most recent version.

Work described
--------------
The text of this thesis describes my work on projects listed below:

 * Alex - Alex Dialogue System Framework(https://github.com/UFAL-DSG/alex) where I added following files and directories:
    * https://github.com/UFAL-DSG/alex/alex/components/asr/kaldi.py
    * https://github.com/UFAL-DSG/alex/alex/tools/kaldi/
    * https://github.com/UFAL-DSG/alex/alex/PublicTransportInfoCs/hclg/
 * The Kaldi toolkit - Speech recognition toolkit where I added following directories:
    * Implementation of OnlineLatgenRecogniser and utilities - https://github.com/UFAL-DSG/pykaldi/tree/master/src/onl-rec/
    * Python wrapper PyOnlineLatgenRecogniser and utilities - https://github.com/UFAL-DSG/pykaldi/tree/master/src/pykaldi/
    * Training scripts for acoustic modelling - https://github.com/UFAL-DSG/pykaldi/tree/master/egs/vystadial/s5/
      The training scripts are also accepted in the Kaldi trunk but they are separated for Czech and English:
         * https://sourceforge.net/p/kaldi/code/HEAD/tree/trunk/egs/vystadial_en/
         * https://sourceforge.net/p/kaldi/code/HEAD/tree/trunk/egs/vystadial_cz/
    * Several demos using OnlineLatgenRecogniser and PyOnlineLatgenRecogniser - https://github.com/UFAL-DSG/pykaldi/tree/master/egs/vystadial/online_demo/

   I am developing the new features in https://github.com/UFAL-DSG/pykaldi repository which I mirror back to my Kaldi sandbox http://sourceforge.net/p/kaldi/code/HEAD/tree/sandbox/oplatek2 which  can be merged to Kaldi trunk. 
 * pyfst - https://github.com/UFAL-DSG/pyfst - Python wrapper of OpenFST, where I improved installation and added several simple functions. Note I forked the original pyfst library.
   
 * Pykaldi-eval - https://github.com/oplatek/pykaldi-eval - Repository for evaluation OnlineLatgenRecogniser written in Ipython notebook. See interesting graphs:
   
 * TODO link to the reference documentation for C++ code in Kaldi
 * TODO link to the reference documentation for Python code in Kaldi
 * TODO link to the reference documentation for Python code in Alex
