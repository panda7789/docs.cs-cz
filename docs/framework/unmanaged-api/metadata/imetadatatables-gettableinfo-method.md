---
title: IMetaDataTables::GetTableInfo – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type:
- apiref
ms.openlocfilehash: 7e60dd9535809ca13f3bbe6ac76f5ea1209df734
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501163"
---
# <a name="imetadatatablesgettableinfo-method"></a>IMetaDataTables::GetTableInfo – metoda
Získá název, velikost řádku, počet řádků, počet sloupců a klíčový index sloupce zadané tabulky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ixTbl`  
 pro Identifikátor tabulky, jejíž vlastnosti se mají vrátit  
  
 `pcbRow`  
 mimo Ukazatel na velikost řádku tabulky v bajtech.  
  
 `pcRows`  
 mimo Ukazatel na počet řádků v tabulce.  
  
 `pcCols`  
 mimo Ukazatel na počet sloupců v tabulce.  
  
 `piKey`  
 mimo Ukazatel na index sloupce klíče nebo hodnotu-1, pokud tabulka neobsahuje žádný klíčový sloupec.  
  
 `ppName`  
 mimo Ukazatel na ukazatel na název tabulky.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataTables – rozhraní](imetadatatables-interface.md)
- [IMetaDataTables2 – rozhraní](imetadatatables2-interface.md)
