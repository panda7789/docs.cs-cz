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
ms.openlocfilehash: a044924810016eea60682b8765aeee448b552f0d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501193"
---
# <a name="imetadatatablesgetcolumninfo-method"></a>IMetaDataTables::GetColumnInfo – metoda
Načte data o zadaném sloupci v zadané tabulce.  
  
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
 pro Index požadované tabulky  
  
 `ixCol`  
 pro Index požadovaného sloupce  
  
 `poCol`  
 mimo Ukazatel na posun sloupce v řádku.  
  
 `pcbCol`  
 mimo Ukazatel na velikost sloupce v bajtech.  
  
 `pType`  
 mimo Ukazatel na typ hodnot ve sloupci.  
  
 `ppName`  
 mimo Ukazatel na ukazatel na název sloupce.  

## <a name="remarks"></a>Poznámky

Vrácený typ sloupce spadá do rozsahu hodnot:

| pType                    | Description   | Pomocná funkce                   |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0.. 63)   | Mezinárodní           | **IsRidType**<br>**IsRidOrToken** |
| `iCodedToken`..`iCodedTokenMax`<br>(64.. 95) | Kódovaný token | **IsCodedTokenType** <br>**IsRidOrToken** |
| `iSHORT`(96)            | Int16         | **IsFixedType**                   |
| `iUSHORT`(97)           | UInt16        | **IsFixedType**                   |
| `iLONG`(98)             | Int32         | **IsFixedType**                   |
| `iULONG`(99)            | UInt32        | **IsFixedType**                   |
| `iBYTE`(100)            | Byte          | **IsFixedType**                   |
| `iSTRING`(101)          | Řetězec        | **IsHeapType**                    |
| `iGUID`(102)            | Identifikátor GUID          | **IsHeapType**                    |
| `iBLOB`(103)            | Objekt blob          | **IsHeapType**                    |

Hodnoty, které jsou uloženy v *haldě* (tj `IsHeapType == true` .), lze číst pomocí:

- `iSTRING`: **IMetadataTables. GetString**
- `iGUID`: **IMetadataTables. GETguid**
- `iBLOB`: **IMetadataTables. Getblob**

> [!IMPORTANT]
> Chcete-li použít konstanty definované v tabulce výše, zahrňte direktivu, kterou `#define _DEFINE_META_DATA_META_CONSTANTS` poskytuje hlavičkový soubor *cor. h* .

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataTables – rozhraní](imetadatatables-interface.md)
- [IMetaDataTables2 – rozhraní](imetadatatables2-interface.md)
