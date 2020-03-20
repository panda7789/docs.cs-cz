---
title: IMetaDataTables::GetColumnInfo – metoda
ms.date: 10/10/2019
api_name:
- IMetaDataTables.GetColumnInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type:
- apiref
ms.openlocfilehash: cc8aac32149fed952737d928e16a8f6efc448c79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177125"
---
# <a name="imetadatatablesgetcolumninfo-method"></a>IMetaDataTables::GetColumnInfo – metoda
Získá data o zadaném sloupci v zadané tabulce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetColumnInfo (
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
## <a name="parameters"></a>Parametry
=======

 `ixTbl`  
 [v] Index požadované tabulky.  
  
 `ixCol`  
 [v] Index požadovaného sloupce.  
  
 `poCol`  
 [out] Ukazatel na posun sloupce v řádku.  
  
 `pcbCol`  
 [out] Ukazatel na velikost sloupce v bajtech.  
  
 `pType`  
 [out] Ukazatel na typ hodnot ve sloupci.  
  
 `ppName`  
 [out] Ukazatel na ukazatel na název sloupce.  

## <a name="remarks"></a>Poznámky

Typ vráceného sloupce spadá do rozsahu hodnot:

| pTyp                    | Popis   | Pomocná funkce                   |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0..63)   | Zbavit           | **ISRIDTyp**<br>**Isridortoken** |
| `iCodedToken`..`iCodedTokenMax`<br>(64..95) | Kódovaný token | **IsCodedTokenType** <br>**Isridortoken** |
| `iSHORT`(96)            | Int16         | **IsFixedType**                   |
| `iUSHORT`(97)           | UInt16        | **IsFixedType**                   |
| `iLONG`(98)             | Int32         | **IsFixedType**                   |
| `iULONG`(99)            | UInt32        | **IsFixedType**                   |
| `iBYTE`(100)            | Byte          | **IsFixedType**                   |
| `iSTRING`(101)          | Řetězec        | **IsHeapType**                    |
| `iGUID`(102)            | Identifikátor GUID          | **IsHeapType**                    |
| `iBLOB`(103)            | Objekt blob          | **IsHeapType**                    |

Hodnoty, které jsou uloženy v `IsHeapType == true` *haldě* (to znamená) lze číst pomocí:

- `iSTRING`: **IMetadataTables.GetString**
- `iGUID`: **IMetadataTables.GetGUID**
- `iBLOB`: **IMetadataTables.GetBlob**

> [!IMPORTANT]
> Chcete-li použít konstanty definované v tabulce `#define _DEFINE_META_DATA_META_CONSTANTS` výše, zadejte direktivu poskytnutou souborem záhlaví *cor.h.*

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataTables – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
