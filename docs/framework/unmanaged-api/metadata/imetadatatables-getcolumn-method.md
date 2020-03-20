---
title: IMetaDataTables::GetColumn – metoda
ms.date: 02/25/2019
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
ms.openlocfilehash: f43d4d1547cbe92f325950e1697dada83b42c4f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177141"
---
# <a name="imetadatatablesgetcolumn-method"></a>IMetaDataTables::GetColumn – metoda
Získá ukazatel na hodnotu obsaženou v buňce zadaného sloupce a řádku v dané tabulce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetColumn (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a>Parametry

 `ixTbl`  
 [v] Index tabulky.  
  
 `ixCol`  
 [v] Index sloupce v tabulce.  
  
 `rid`  
 [v] Index řádku v tabulce.  
  
 `pVal`  
 [out] Ukazatel na hodnotu v buňce.  

## <a name="remarks"></a>Poznámky

Interpretace hodnoty vrácené prostřednictvím `pVal` závisí na typu sloupce. Typ sloupce lze určit voláním [iMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).

- Metoda **GetColumn** automaticky převede sloupce typu **Rid** nebo **CodedToken** na plné 32bitové `mdToken` hodnoty.
- Také automaticky převede 8bitové nebo 16bitové hodnoty na plné 32bitové hodnoty.
- Pro sloupce typu *haldy* vrácené *pVal* bude index do odpovídající haldy.

| Typ sloupce              | pVal obsahuje | Poznámka                          |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0..63)  | mdToken     | *pVal* bude obsahovat úplný token. Funkce automaticky převede Rid do úplného tokenu. |
| `iCodedToken`..`iCodedTokenMax`<br>(64..95) | mdToken | Po návratu bude *pVal* obsahovat úplný token. Funkce automaticky dekomprimuje CodedToken do úplného tokenu. |
| `iSHORT`(96)            | Int16         | Automaticky se prodlužuje na 32bitový.  |
| `iUSHORT`(97)           | UInt16        | Automaticky se prodlužuje na 32bitový.  |
| `iLONG`(98)             | Int32         |                                        |
| `iULONG`(99)            | UInt32        |                                        |
| `iBYTE`(100)            | Byte          | Automaticky se prodlužuje na 32bitový.  |
| `iSTRING`(101)          | Index haldy řetězce | *pVal* je index do haldy String. Pomocí [hodnot IMetadataTables::GetString](imetadatatables-getstring-method.md) získáte skutečnou hodnotu řetězce sloupce. |
| `iGUID`(102)            | Index haldy Guid | *pVal* je index do haldy Guid. Pomocí [iMetadataTables::GetGuid](imetadatatables-getguid-method.md) získat skutečnou hodnotu sloupce Guid. |
| `iBLOB`(103)            | Index haldy objektu blob | *pVal* je index do haldy objektu blob. Pomocí [tabulky MetadataTables::GetBlob](imetadatatables-getblob-method.md) získáte skutečnou hodnotu objektu blob sloupce. |
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataTables – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
