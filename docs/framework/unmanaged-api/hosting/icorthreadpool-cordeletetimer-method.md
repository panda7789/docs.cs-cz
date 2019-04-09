---
title: ICorThreadpool::CorDeleteTimer – metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorDeleteTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeleteTimer
helpviewer_keywords:
- ICorThreadpool::CorDeleteTimer method [.NET Framework hosting]
- CorDeleteTimer method [.NET Framework hosting]
ms.assetid: 74847c35-7ca1-466a-b750-b25e7b03d100
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 098c23dd0ddff4342aa4cefbaa4e149ed95a1cb3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178344"
---
# <a name="icorthreadpoolcordeletetimer-method"></a>ICorThreadpool::CorDeleteTimer – metoda
Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CorDeleteTimer (  
    [in]  HANDLE Timer,  
    [in]  HANDLE CompletionEvent,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorThreadpool – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
