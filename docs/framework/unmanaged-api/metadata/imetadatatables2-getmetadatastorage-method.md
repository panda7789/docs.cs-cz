---
title: IMetaDataTables2::GetMetaDataStorage – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStorage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStorage
helpviewer_keywords:
- GetMetaDataStorage method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStorage method [.NET Framework metadata]
ms.assetid: 667a6d1e-753d-4ea2-8fd8-a8337d1bb9cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f12243571262ad7511795c48721617932fc6b30b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161405"
---
# <a name="imetadatatables2getmetadatastorage-method"></a>IMetaDataTables2::GetMetaDataStorage – metoda
Získá velikost a obsah metadata uložená v zadaném oddílu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppvMd`  
 [out v] Ukazatel na oddíl metadat.  
  
 `pcbMd`  
 [out] Velikost datový proud metadat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataTables2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
- [IMetaDataTables – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
