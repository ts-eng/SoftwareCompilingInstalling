conda create -n smartrobot python=3.8  
conda activate smartrobot  
sudo apt-get install libxcb-xinerama0  
cd datamanager/labelImg/  
pip download labelImg  
cd ../../  
pip install labelImg --find-links datamanager/labelImg/ --no-index  
cd modelbuilder/deps  
pip download -r ../requirements.txt  
cd ../../
pip install -r modelbuilder/requirements.txt --find-links modelbuilder/deps/ --no-index
