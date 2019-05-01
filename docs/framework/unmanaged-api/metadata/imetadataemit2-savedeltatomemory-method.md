---
title: IMetaDataEmit2::SaveDeltaToMemory – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToMemory
helpviewer_keywords:
- SaveDeltaToMemory method [.NET Framework metadata]
- IMetaDataEmit2::SaveDeltaToMemory method [.NET Framework metadata]
ms.assetid: e2146726-0084-4c9e-a2d2-e8d461b13b21
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fa95a737747e9153eb844cddd8e0684585b9108b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049970"
---
# <a name="imetadataemit2savedeltatomemory-method"></a>IMetaDataEmit2::SaveDeltaToMemory – metoda
Uloží změny z aktuální relace edit-and-continue do paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,   
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbData`  
 [out] Adresa ve kterém se má začít psát metadata delta.  
  
 `cbData`  
 [in] Velikost změny. Použití [imetadataemit2::getdeltasavesize –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) k určení velikosti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
