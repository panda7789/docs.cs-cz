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
ms.openlocfilehash: 17305f2c088dd6f479da4c823d3db0fd50c0b3d7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443220"
---
# <a name="imetadatatables-interface"></a>IMetaDataTables – rozhraní
Poskytuje metody pro ukládání a načítání informací o metadatech v tabulkách.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetBlob – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|Získá ukazatel na binární rozsáhlý objekt (BLOB) v zadaném indexu sloupce.|  
|[GetBlobHeapSize – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|Získá velikost haldy objektů BLOB v bajtech.|  
|[GetCodedTokenInfo – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|Získá ukazatel na pole tokenů přidružené k zadanému indexu řádků.|  
|[GetColumn – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|Získá ukazatel na hodnoty obsažené ve sloupci v zadaném indexu sloupce v tabulce se zadaným indexem tabulky.|  
|[GetColumnInfo – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|Načte data o zadaném sloupci v zadané tabulce.|  
|[GetGuid – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|Získá identifikátor GUID z řádku na zadaném indexu.|  
|[GetGuidHeapSize – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|Získá velikost haldy GUID (v bajtech).|  
|[GetNextBlob – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|Získá index dalšího objektu BLOB v tabulce.|  
|[GetNextGuid – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|Získá index další hodnoty GUID ve sloupci aktuální tabulky.|  
|[GetNextString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|Získá index dalšího řetězce ve sloupci aktuální tabulky.|  
|[GetNextUserString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|Získá index řádku, který obsahuje další pevně zakódovaný řetězec ve sloupci aktuální tabulky.|  
|[GetNumTables – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|Získá počet tabulek v rozsahu aktuální instance `IMetaDataTables`.|  
|[GetRow – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|Získá řádek v zadaném indexu řádku v tabulce se zadaným indexem tabulky.|  
|[GetString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|Získá řetězec na zadaném indexu ze sloupce tabulky v aktuálním oboru odkazů.|  
|[GetStringHeapSize – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|Získá velikost haldy řetězce v bajtech.|  
|[GetTableIndex – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|Získá index pro tabulku, na kterou odkazuje zadaný token.|  
|[GetTableInfo – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|Získá název, velikost řádku, počet řádků, počet sloupců a klíčový index sloupce tabulky v zadaném indexu tabulky.|  
|[GetUserString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|Získá pevně zakódovaný řetězec na zadaném indexu ve sloupci řetězce v aktuálním oboru.|  
|[GetUserStringHeapSize – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|Získá velikost haldy řetězců uživatele v bajtech.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataTables2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
