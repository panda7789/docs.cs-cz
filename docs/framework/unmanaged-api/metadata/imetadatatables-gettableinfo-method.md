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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea617668a72413f3387a35fe009b37fa15d03354
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatatablesgettableinfo-method"></a>IMetaDataTables::GetTableInfo – metoda
Získá název, velikost řádku, počet řádků, počet sloupců a index klíče sloupců zadané tabulky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ixTbl`  
 [v] Identifikátor tabulky, jehož vlastnosti chcete vrátit.  
  
 `pcbRow`  
 [out] Ukazatel na velikost v bajtech řádku tabulky.  
  
 `pcRows`  
 [out] Ukazatel na počet řádků v tabulce.  
  
 `pcCols`  
 [out] Ukazatel na počet sloupců v tabulce.  
  
 `piKey`  
 [out] Ukazatel na index klíče sloupce nebo -1, pokud tabulka nemá žádný klíčový sloupec.  
  
 `ppName`  
 [out] Ukazatel na ukazatel na název tabulky.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataTables – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [IMetaDataTables2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
