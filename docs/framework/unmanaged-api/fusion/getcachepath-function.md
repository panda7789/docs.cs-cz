---
title: GetCachePath – funkce
ms.date: 03/30/2017
api_name:
- GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- GetCachePath
helpviewer_keywords:
- GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type:
- apiref
ms.openlocfilehash: 13e1468ef5a48f18910c1f8082cdd7c4849da14a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132697"
---
# <a name="getcachepath-function"></a>GetCachePath – funkce
Načte cestu k sestavení v mezipaměti pomocí zadaných příznaků.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a>Parametry  
 `dwCacheFlags`  
 pro Hodnota [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) , která označuje zdroj sestavení v mezipaměti.  
  
 `pwzCachePath`  
 mimo Vrácený ukazatel na cestu.  
  
 `pcchPath`  
 [in, out] Požadovaná maximální délka `pwzCachePath`a po návratu se jedná o skutečnou délku `pwzCachePath`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Fusion. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ASM_CACHE_FLAGS – výčet](asm-cache-flags-enumeration.md)
- [Globální statické funkce pro fúze](fusion-global-static-functions.md)
