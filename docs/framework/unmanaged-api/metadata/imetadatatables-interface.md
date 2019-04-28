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
ms.openlocfilehash: 2b2298e2d67e8a50e11d53d864f0e78f3b549e45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645175"
---
# <a name="imetadatatables-interface"></a>IMetaDataTables – rozhraní
Poskytuje metody pro ukládání a načítání informací o metadatech v tabulkách.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetBlob – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|Získá ukazatel na binární rozsáhlý objekt (BLOB) na zadaný sloupec indexu.|  
|[GetBlobHeapSize – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|Získá velikost v bajtech binárního rozsáhlého objektu haldy.|  
|[GetCodedTokenInfo – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|Získá ukazatel na pole tokenů přidružený index zadaný řádek.|  
|[GetColumn – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|Získá ukazatel na hodnoty obsažené v sloupci indexu zadaný sloupec v tabulce indexu zadané tabulky.|  
|[GetColumnInfo – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|Získá data o zadaný sloupec zadané tabulky.|  
|[GetGuid – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|Získá identifikátor GUID z řádku v zadaném indexu.|  
|[GetGuidHeapSize – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|Získá velikost v bajtech haldy GUID.|  
|[GetNextBlob – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|Získá index další objektů BLOB v tabulce.|  
|[GetNextGuid – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|Získá index další hodnota identifikátoru GUID v aktuálním sloupci tabulky.|  
|[GetNextString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|Získá index další řetězce v aktuálním sloupci tabulky.|  
|[GetNextUserString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|Získá index řádku, který obsahuje další pevně zakódované řetězce v aktuálním sloupci tabulky.|  
|[GetNumTables – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|Získá počet tabulek v rámci aktuálního `IMetaDataTables` instance.|  
|[GetRow – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|Získá řádek indexu zadaný řádek v tabulce indexu zadané tabulky.|  
|[GetString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|Získá řetězec v zadaném indexu ze sloupce tabulky v aktuálním oboru odkaz.|  
|[GetStringHeapSize – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|Získá velikost v bajtech, řetězec haldy.|  
|[GetTableIndex – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|Získá index pro tabulku odkazuje zadaný token.|  
|[GetTableInfo – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|Získá název, velikost řádku, počet řádků, počet sloupců a index sloupce klíče tabulky indexu zadané tabulky.|  
|[GetUserString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|Získá řetězec pevně zakódované v zadaném indexu ve sloupci řetězce v aktuálním oboru.|  
|[GetUserStringHeapSize – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|Získá velikost v bajtech, řetězec haldy uživatele.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataTables2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
