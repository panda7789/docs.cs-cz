---
title: ICLRRuntimeInfo::IsLoadable – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
ms.openlocfilehash: 9339bb974c261e62502c760dfaf45651573cbe1a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136378"
---
# <a name="iclrruntimeinfoisloadable-method"></a>ICLRRuntimeInfo::IsLoadable – metoda
Určuje, zda lze modul runtime spojený s tímto rozhraním načíst do aktuálního procesu, přičemž vezme v úvahu jiné moduly runtime, které mohou být do procesu již načteny.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbLoadable`  
 [out] `true`, jestli se tento modul runtime mohl načíst do aktuálního procesu. v opačném případě `false`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pbLoadable` je null.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je již do procesu načten jiný modul runtime a modul runtime přidružený k tomuto rozhraní lze načíst pro vnitroprocesové souběžné spouštění, `pbLoadable` vrátí `true`. Pokud tyto dva moduly runtime nemohou běžet souběžně v rámci procesu, `pbLoadable` vrátí `false`. Například modul CLR (Common Language Runtime) verze 4 může běžet souběžně v rámci stejného procesu s CLR verze 2,0 nebo CLR verze 1,1. CLR verze 1,1 a CLR verze 2,0 však nemůže spustit souběžný proces souběžného zpracování.  
  
 Pokud nejsou do procesu načteny žádné moduly runtime, tato metoda vždy vrátí `true`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRRuntimeInfo – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
