---
title: DestroyICeeFileGen – funkce
ms.date: 03/30/2017
api_name:
- DestroyICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- DestroyICeeFileGen
helpviewer_keywords:
- DestroyICeeFileGen function [.NET Framework hosting]
ms.assetid: dc1e2235-e721-4cb2-a0b8-6b0c030d7bab
topic_type:
- apiref
ms.openlocfilehash: 4eb878b61b72378bc6870af7f2cd09f0b6943b13
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136504"
---
# <a name="destroyiceefilegen-function"></a>DestroyICeeFileGen – funkce
Odstraní objekt [ICeeFileGen –](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) .  
  
 Tato funkce se už nepoužívá v .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ceeFileGen`  
 pro Objekt `ICeeFileGen`, který se má zničit.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí standardní kódy chyb modelu COM.  
  
## <a name="remarks"></a>Poznámky  
 `DestroyICeeFileGen` zničí objekt `ICeeFileGen` vytvořený funkcí [CreateICeeFileGen –](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** ICeeFileGen –. h  
  
 **Knihovna:** MSCorPE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
