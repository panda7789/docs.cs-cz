---
title: ICLRMetaHost::GetRuntime – metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
ms.openlocfilehash: d482e25c7bf0f028e2478c8e7b7863bc54d7aeb9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504189"
---
# <a name="iclrmetahostgetruntime-method"></a>ICLRMetaHost::GetRuntime – metoda
Získá rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , které odpovídá konkrétní verzi modulu CLR (Common Language Runtime). Tato metoda nahrazuje funkci [CorBindToRuntimeEx –](corbindtoruntimeex-function.md) použitou s příznakem [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in] REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzVersion`  
 pro Verze kompilace .NET Framework uložená v metadatech ve formátu "v*A*. *B*[.* X*] ". *A*, *B*a *X* jsou desítková čísla, která odpovídají hlavní verzi, dílčí verzi a číslo buildu.  
  
> [!NOTE]
> Tento parametr se musí shodovat s názvem adresáře pro verzi .NET Framework, jak se zobrazuje v části C:\Windows\Microsoft.NET\Framework nebo C:\Windows\Microsoft.NET\Framework64..  
  
 Příklady hodnot jsou "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" a "v 4.0". *X*, kde *x* závisí na nainstalovaném čísle sestavení. Předpona "v" je povinná.  
  
 `riid`  
 pro Identifikátor požadovaného rozhraní. V současné době je jediná platná hodnota pro tento parametr IID_ICLRRuntimeInfo.  
  
 `ppRuntime`  
 mimo Ukazatel na rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , které odpovídá požadovanému modulu runtime.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pwzVersion`nebo `ppRuntime` má hodnotu null.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda komunikuje konzistentně se staršími rozhraními, jako je rozhraní [ICorRuntimeHost](icorruntimehost-interface.md) a starší funkce, jako jsou zastaralé `CorBindTo*` funkce (viz téma [zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md) v rozhraní API pro hostování .NET Framework 2,0). To znamená, že moduly runtime načtené pomocí starší verze rozhraní API jsou viditelné pro nové rozhraní API a moduly runtime načtené pomocí nového rozhraní API jsou viditelné pro starší rozhraní API.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRMetaHost – rozhraní](iclrmetahost-interface.md)
- [Zastaralá rozhraní a třídy typu Coclass pro hostování CLR](deprecated-clr-hosting-interfaces-and-coclasses.md)
- [Rozhraní hostování CLR](clr-hosting-interfaces.md)
- [Zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md)
- [Hosting](index.md)
