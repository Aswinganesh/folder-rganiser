import os
import collections

    DOWNLOAD_PATH = os.path.join(os.path.expanduser('~'),'Downloads')

    file_map = collections.defaultdict()
    for filename in os.listdir(DOWNLOAD_PATH):
        filetype = filename.split('.')[-1]
        file_map.setdefault(filetype,[]).append(filename)

    for foldername,folderitems in file_map.items():
        folderpath = os.path.join(DOWNLOAD_PATH,foldername)
        if not os.path.exists(folderpath):
            os.mkdir(folderpath)

        for folderitem in folderitems:
            source = os.path.join(DOWNLOAD_PATH,folderitem)
            destination = os.path.join(folderpath,folderitem)
            print(f'Moving{source} to {destination}')
