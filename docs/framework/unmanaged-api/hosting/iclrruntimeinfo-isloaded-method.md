---
title: ICLRRuntimeInfo::IsLoaded – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoaded
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type:
- apiref
ms.openlocfilehash: 45e27ac3c2d4912d2ed3e5d43ea3020b9db5dbdc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504027"
---
# <a name="iclrruntimeinfoisloaded-method"></a>ICLRRuntimeInfo::IsLoaded – metoda
Označuje, zda je modul CLR (Common Language Runtime) přidružený k rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) načten do procesu. Modul runtime lze načíst bez nutnosti také spuštění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a>Parametry  
 `hndProcess`  
 pro Popisovač procesu.  
  
 `pbLoaded`  
 [out] `true` Pokud je modul CLR načten do procesu; v opačném případě `false` .  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pbLoaded`má hodnotu null.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je zpětně kompatibilní s následujícími funkcemi a rozhraními:  
  
- Rozhraní [ICorRuntimeHost](icorruntimehost-interface.md) (v rozhraní API pro hostování .NET Framework verze 1).  
  
- Rozhraní [ICLRRuntimeHost](iclrruntimehost-interface.md) (rozhraní API pro hostování .NET Framework 2,0).  
  
- Zastaralé `CorBindTo*` funkce (viz téma [zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md) v rozhraní API pro hostování .NET Framework 2,0).  
  
 Hostitel může zavolat jednu z zastaralých `CorBindTo*` funkcí, jako je například funkce [CorBindToRuntime](corbindtoruntime-function.md) , pro vytvoření instance konkrétní verze modulu CLR. Hostitel pak může zavolat metodu [ICLRMetaHost:: GetRuntime](iclrmetahost-getruntime-method.md) a zadat stejné číslo verze pro získání rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .  
  
 Pokud hostitel pak zavolá `IsLoaded` metodu v vráceném rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , `pbLoaded` vrátí hodnotu `true` . jinak vrátí `false` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRRuntimeInfo – rozhraní](iclrruntimeinfo-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
- [Hosting](index.md)
