conda create -n smartrobot python=3.8  
conda activate smartrobot  
cd datamanager/labelImg/  
pip download labelImg  
cd ../../  
pip install labelImg --find-links datamanager/labelImg/ --no-index  
