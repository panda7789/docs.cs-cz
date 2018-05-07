---
title: IMetaDataFilter::IsTokenMarked – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.IsTokenMarked
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::IsTokenMarked
helpviewer_keywords:
- IMetaDataFilter::IsTokenMarked method [.NET Framework metadata]
- IsTokenMarked method [.NET Framework metadata]
ms.assetid: 7d90dcee-0206-4540-807b-06982fe65f1a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5bf5149e8e42a810a6a490767638b374f66b5679
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatafilteristokenmarked-method"></a>IMetaDataFilter::IsTokenMarked – metoda
Získá hodnotu označující, zda zadaná metadata token byla označena jako zpracovaná.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,   
    [out] BOOL     *pIsMarked  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tk`  
 [v] Token k prozkoumání pro zpracování značky.  
  
 `pIsMarked`  
 [out] Hodnotu, která je `true` Pokud `tk` byl zpracován; jinak hodnota `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataFilter – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
