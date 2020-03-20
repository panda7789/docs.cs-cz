---
title: ICLRRuntimeHost::ExecuteInDefaultAppDomain – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type:
- apiref
ms.openlocfilehash: 1a1bc7609042422de876fe167a9e61655aaf62b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176406"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a>ICLRRuntimeHost::ExecuteInDefaultAppDomain – metoda
Volá zadanou metodu zadaného typu v zadaném spravovaném sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzAssemblyPath`  
 [v] Cesta <xref:System.Reflection.Assembly> k, která definuje, <xref:System.Type> jehož metoda má být vyvolána.  
  
 `pwzTypeName`  
 [v] <xref:System.Type> Název, který definuje metodu vyvolat.  
  
 `pwzMethodName`  
 [v] Název metody vyvolat.  
  
 `pwzArgument`  
 [v] Parametr řetězce předat metodě.  
  
 `pReturnValue`  
 [out] Hodnota celéčíslo vrácené vztažnou metodou.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`ExecuteInDefaultAppDomain`úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Běžný jazyk runtime (CLR) nebyl načten do procesu nebo CLR je ve stavu, ve kterém nelze spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Časový čas hovoru byl vypován.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena, zatímco na ní čekalo blokované vlákno nebo vlákno.|  
|E_fail|Došlo k neznámému katastrofickému selhání. Pokud metoda vrátí E_FAIL, seznam odvolaných hodnot již není použitelný v rámci procesu. Následná volání metod hostování vrátí HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Metoda vyvolaná musí mít následující podpis:  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 kde `pwzMethodName` představuje název vztažné `pwzArgument` metody a představuje hodnotu řetězce předanou jako parametr této metodě. Pokud je hodnota HRESULT nastavena na S_OK, `pReturnValue` je nastavena na hodnotu celéčíslo vrácenou vztažnou metodou. V `pReturnValue` opačném případě není nastavena.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
