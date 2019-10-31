---
title: CreateICeeFileGen – funkce
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
ms.openlocfilehash: de27851b4afc3eccad46531848c68723bff346d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136821"
---
# <a name="createiceefilegen-function"></a>CreateICeeFileGen – funkce
Vytvoří objekt [ICeeFileGen –](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) .  
  
 Tato funkce se už nepoužívá v .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ceeFileGen`  
 mimo Ukazatel na adresu nového objektu `ICeeFileGen`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí standardní kódy chyb modelu COM.  
  
## <a name="remarks"></a>Poznámky  
 Objekt `ICeeFileGen` slouží k vytvoření přenosných spustitelných souborů (PE) pro modul CLR (Common Language Runtime).  
  
 Po dokončení volejte funkci [DestroyICeeFileGen –](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) pro zničení objektu `ICeeFileGen`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** ICeeFileGen –. h  
  
 **Knihovna:** MSCorPE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
