# python
python提取数据
from osgeo import gdal
import shapefile

path_dem = '***\\***.tif'

def readDataFormat(raw_path):
    path = str(raw_path)
    pathlist = path.split('.')
    num = len(pathlist)

    return pathlist[num-1]


def readRawData(path_data):
    dataformat = readDataFormat(path_data)
    print(path_data)
    if str(dataformat) == 'img':
        geo = gdal.Open(str(path_data))
        raw_data = geo.ReadAsArray()
        data = raw_data.astype(np.float32)

    elif str(dataformat) == 'tif':
        raw_data = gdal.Open(str(path_data))
        data = raw_data.ReadAsArray()

    return data

raw_dem = readRawData(str(path_dem))
