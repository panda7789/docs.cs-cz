---
title: IMetaDataTables – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables
helpviewer_keywords:
- IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1a11c0b697a32b184a2c4a60c2f2c88a4b47aaf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatatables-interface"></a>IMetaDataTables – rozhraní
Poskytuje metody pro ukládání a načítání informací metadat v tabulkách.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetBlob – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|Získá ukazatel na binární rozsáhlý objekt (binární rozsáhlý OBJEKT) v indexu zadaný sloupec.|  
|[GetBlobHeapSize – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|Získá velikost v bajtech haldě objektů BLOB.|  
|[GetCodedTokenInfo – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|Získá ukazatel na pole tokeny přidružený index zadaný řádku.|  
|[GetColumn – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|Získá ukazatel na hodnoty obsažené v sloupce v indexu zadaný sloupec, v tabulce u zadané tabulky indexu.|  
|[GetColumnInfo – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|Získá data o zadaný sloupec zadané tabulky.|  
|[GetGuid – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|Získá identifikátor GUID z řádek na pozici se zadaným indexem.|  
|[GetGuidHeapSize – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|Získá velikost v bajtech haldě identifikátor GUID.|  
|[GetNextBlob – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|Získá index další objektů BLOB v tabulce.|  
|[GetNextGuid – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|Získá index další hodnota identifikátoru GUID v aktuální sloupec tabulky.|  
|[GetNextString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|Získá index další řetězce v aktuálním sloupec tabulky.|  
|[GetNextUserString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|Získá index řádku, který obsahuje další pevně řetězce v aktuálním sloupec tabulky.|  
|[GetNumTables – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|Získá počet tabulek v rozsahu aktuální `IMetaDataTables` instance.|  
|[GetRow – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|Získá řádek indexem zadaný řádek v tabulce u zadané tabulky indexu.|  
|[GetString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|Získá řetězec v zadaném indexu ze sloupce tabulky v aktuálním oboru odkaz.|  
|[GetStringHeapSize – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|Získá velikost v bajtech haldy řetězce.|  
|[GetTableIndex – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|Získá index pro tabulku odkazuje zadaný token.|  
|[GetTableInfo – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|Získá název, velikost řádku, počet řádků, počet sloupců a index sloupce klíče tabulky v indexu zadané tabulky.|  
|[GetUserString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|Získá řetězec pevně v zadaném indexu ve sloupci řetězce v aktuálním oboru.|  
|[GetUserStringHeapSize – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|Získá velikost v bajtech haldě řetězec uživatele.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataTables2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
