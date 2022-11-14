# Selection-of-CCTV-location-in-Gimhae-_COMPAS

from geoband.API import *
GetCompasData('SBJ_2206_001', '1', 'data/1.김해시_CCTV설치현황.csv')
GetCompasData('SBJ_2206_001', '2', 'data/2.김해시_주차장현황.csv')
GetCompasData('SBJ_2206_001', '3', 'data/3.김해시_성연령별_요일별_유동인구.zip')
GetCompasData('SBJ_2206_001', '25', 'data/4.김해시_112신고이력(격자매핑).csv')
GetCompasData('SBJ_2206_001', '5', 'data/5.김해시_격자(100X100).geojson')
GetCompasData('SBJ_2206_001', '6', 'data/6.김해시_보안등설치현황.csv')
GetCompasData('SBJ_2206_001', '28', 'data/7.김해시_안전비상벨설치현황.csv')
GetCompasData('SBJ_2206_001', '26', 'data/8.김해시_공원현황.geojson')
GetCompasData('SBJ_2206_001', '9', 'data/9.김해시_하천현황.geojson')
GetCompasData('SBJ_2206_001', '22', 'data/10.김해시_성연령별_거주인구격자.geojson')
GetCompasData('SBJ_2206_001', '11', 'data/11.김해시_외국인_읍면동별_격자.geojson')
GetCompasData('SBJ_2206_001', '23', 'data/12.김해시_건물노후도.geojson')
GetCompasData('SBJ_2206_001', '13', 'data/13.김해시_도로명주소(건물).geojson')
GetCompasData('SBJ_2206_001', '14', 'data/14.김해시_법정경계(읍면동).geojson')
GetCompasData('SBJ_2206_001', '15', 'data/15.김해시_행정경계(읍면동).geojson')
GetCompasData('SBJ_2206_001', '27', 'data/16.김해시_토지소유정보.geojson')
GetCompasData('SBJ_2206_001', '17', 'data/17.김해시_어린이집현황.csv')
GetCompasData('SBJ_2206_001', '18', 'data/18.김해시_유치원현황.csv')
GetCompasData('SBJ_2206_001', '19', 'data/19.김해시_학교(초,중,고)현황.csv')
GetCompasData('SBJ_2206_001', '24', 'data/20.김해시_치안_유관업종_현황.csv')
GetCompasData('SBJ_2206_001', '21', 'data/21.김해시_아동안전지킴이집_현황.csv')
# zip 파일 풀기
import zipfile

with zipfile.ZipFile('data/3.김해시_성연령별_요일별_유동인구.zip', 'r') as zf:
    zipinfo = zf.infolist()
    for info in zipinfo:
        info.filename = info.filename.encode('cp437').decode('euc-kr')
        zf.extract(info, './data/')
# 라이브러리
import json
import numpy as np
import pandas as pd
import geopandas as gpd
import folium
import matplotlib.pyplot as plt
import cartopy.crs as ccrs
"""
df_1 = pd.read_csv('data/1.김해시_CCTV설치현황.csv')
df_2 = pd.read_csv('data/2.김해시_주차장현황.csv')
df_3_1 = pd.read_csv('data/김해시_요일별_성연령별_유동인구.csv')
df_3_2 = pd.read_csv('data/김해시_유동인구_CELLPOINT.csv')
df_4 = pd.read_csv('data/4.김해시_112신고이력(격자매핑).csv')
df_5 = gpd.read_file('data/5.김해시_격자(100X100).geojson')
df_6 = pd.read_csv('data/6.김해시_보안등설치현황.csv')
df_7 = pd.read_csv('data/7.김해시_안전비상벨설치현황.csv')
df_8 = gpd.read_file('data/8.김해시_공원현황.geojson')
df_9 = gpd.read_file('data/9.김해시_하천현황.geojson')
df_10 = gpd.read_file('data/10.김해시_성연령별_거주인구격자.geojson')
df_11 = gpd.read_file('data/11.김해시_외국인_읍면동별_격자.geojson')
df_12 = gpd.read_file('data/12.김해시_건물노후도.geojson')
df_13 = gpd.read_file('data/13.김해시_도로명주소(건물).geojson')
df_14 = gpd.read_file('data/14.김해시_법정경계(읍면동).geojson')
df_15 = gpd.read_file('data/15.김해시_행정경계(읍면동).geojson')
df_16 = gpd.read_file('data/16.김해시_토지소유정보.geojson')
df_17 = pd.read_csv('data/17.김해시_어린이집현황.csv')
df_18 = pd.read_csv('data/18.김해시_유치원현황.csv')
df_19 = pd.read_csv('data/19.김해시_학교(초,중,고)현황.csv')
df_20 = pd.read_csv('data/20.김해시_치안_유관업종_현황.csv')
df_21 = pd.read_csv('data/21.김해시_아동안전지킴이집_현황.csv')
"""
