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
ms.openlocfilehash: 2105033e684ec172e24adfb14bcab7668b388af3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501118"
---
# <a name="imetadatatables-interface"></a>IMetaDataTables – rozhraní
Poskytuje metody pro ukládání a načítání informací o metadatech v tabulkách.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[GetBlob – metoda](imetadatatables-getblob-method.md)|Získá ukazatel na binární rozsáhlý objekt (BLOB) v zadaném indexu sloupce.|  
|[GetBlobHeapSize – metoda](imetadatatables-getblobheapsize-method.md)|Získá velikost haldy objektů BLOB v bajtech.|  
|[GetCodedTokenInfo – metoda](imetadatatables-getcodedtokeninfo-method.md)|Získá ukazatel na pole tokenů přidružené k zadanému indexu řádků.|  
|[GetColumn – metoda](imetadatatables-getcolumn-method.md)|Získá ukazatel na hodnoty obsažené ve sloupci v zadaném indexu sloupce v tabulce se zadaným indexem tabulky.|  
|[GetColumnInfo – metoda](imetadatatables-getcolumninfo-method.md)|Načte data o zadaném sloupci v zadané tabulce.|  
|[GetGuid – metoda](imetadatatables-getguid-method.md)|Získá identifikátor GUID z řádku na zadaném indexu.|  
|[GetGuidHeapSize – metoda](imetadatatables-getguidheapsize-method.md)|Získá velikost haldy GUID (v bajtech).|  
|[GetNextBlob – metoda](imetadatatables-getnextblob-method.md)|Získá index dalšího objektu BLOB v tabulce.|  
|[GetNextGuid – metoda](imetadatatables-getnextguid-method.md)|Získá index další hodnoty GUID ve sloupci aktuální tabulky.|  
|[GetNextString – metoda](imetadatatables-getnextstring-method.md)|Získá index dalšího řetězce ve sloupci aktuální tabulky.|  
|[GetNextUserString – metoda](imetadatatables-getnextuserstring-method.md)|Získá index řádku, který obsahuje další pevně zakódovaný řetězec ve sloupci aktuální tabulky.|  
|[GetNumTables – metoda](imetadatatables-getnumtables-method.md)|Získá počet tabulek v rozsahu aktuální `IMetaDataTables` instance.|  
|[GetRow – metoda](imetadatatables-getrow-method.md)|Získá řádek v zadaném indexu řádku v tabulce se zadaným indexem tabulky.|  
|[GetString – metoda](imetadatatables-getstring-method.md)|Získá řetězec na zadaném indexu ze sloupce tabulky v aktuálním oboru odkazů.|  
|[GetStringHeapSize – metoda](imetadatatables-getstringheapsize-method.md)|Získá velikost haldy řetězce v bajtech.|  
|[GetTableIndex – metoda](imetadatatables-gettableindex-method.md)|Získá index pro tabulku, na kterou odkazuje zadaný token.|  
|[GetTableInfo – metoda](imetadatatables-gettableinfo-method.md)|Získá název, velikost řádku, počet řádků, počet sloupců a klíčový index sloupce tabulky v zadaném indexu tabulky.|  
|[GetUserString – metoda](imetadatatables-getuserstring-method.md)|Získá pevně zakódovaný řetězec na zadaném indexu ve sloupci řetězce v aktuálním oboru.|  
|[GetUserStringHeapSize – metoda](imetadatatables-getuserstringheapsize-method.md)|Získá velikost haldy řetězců uživatele v bajtech.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](metadata-interfaces.md)
- [IMetaDataTables2 – rozhraní](imetadatatables2-interface.md)
