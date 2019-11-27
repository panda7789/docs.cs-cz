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
ms.openlocfilehash: 376b9ff09ad38ca43d57fcf064458e0331da8aad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441995"
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
 pro Index tabulky  
  
 `ixCol`  
 pro Index sloupce v tabulce  
  
 `rid`  
 pro Index řádku v tabulce  
  
 `pVal`  
 mimo Ukazatel na hodnotu v buňce.  
 
## <a name="remarks"></a>Poznámky

Interpretace hodnoty vrácené prostřednictvím `pVal` závisí na typu sloupce. Typ sloupce lze určit voláním [IMetaDataTables. GetColumnInfo](imetadatatables-getcolumninfo-method.md).

- Metoda **GetColumn** automaticky převede sloupce typu **RID** nebo **CodedToken** na úplné hodnoty 32 `mdToken`.
- Také automaticky převádí 8bitové nebo 16bitové hodnoty na hodnoty Full 32-bit. 
- Pro sloupce typu *haldy* bude vrácená *Pval* index do odpovídající haldy.

| Typ sloupce              | pVal obsahuje | Komentář                          |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0.. 63)  | mdToken     | *Pval* bude obsahovat úplný token. Funkce automaticky převede identifikátor RID na úplný token. |
| `iCodedToken`..`iCodedTokenMax`<br>(64.. 95) | mdToken | Po návratu bude *Pval* obsahovat úplný token. Funkce automaticky dekomprimuje CodedToken na úplný token. |
| `iSHORT` (96)            | Int16         | Automaticky přihlašovat-rozšířené na 32-bit.  |
| `iUSHORT` (97)           | UInt16        | Automaticky přihlašovat-rozšířené na 32-bit.  |
| `iLONG` (98)             | Datový typ Int32         |                                        | 
| `iULONG` (99)            | UInt32        |                                        |
| `iBYTE` (100)            | Byte          | Automaticky přihlašovat-rozšířené na 32-bit.  |
| `iSTRING` (101)          | Index haldy řetězců | *Pval* je index haldy řetězců. K získání skutečné hodnoty řetězce sloupce použijte [IMetadataTables:: GetString](imetadatatables-getstring-method.md) . |
| `iGUID` (102)            | Index haldy GUID | *Pval* je index haldy identifikátoru GUID. K získání skutečné hodnoty GUID sloupce použijte [IMetadataTables:: GetGUID](imetadatatables-getguid-method.md) . |
| `iBLOB` (103)            | Index haldy objektů BLOB | *Pval* je index haldy objektů BLOB. K získání skutečné hodnoty objektu BLOB sloupce použijte [IMetadataTables:: getblob](imetadatatables-getblob-method.md) . |
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataTables – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
