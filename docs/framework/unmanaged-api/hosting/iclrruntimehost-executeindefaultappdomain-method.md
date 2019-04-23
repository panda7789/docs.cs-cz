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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e6805dc67f7ec5ceb8c67d77462a0200b6c0317
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59205902"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a>ICLRRuntimeHost::ExecuteInDefaultAppDomain – metoda
Volá metodu zadané zadaného typu v zadaném spravovaná sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Cesta k <xref:System.Reflection.Assembly> , který definuje <xref:System.Type> jehož metoda má být vyvolána.  
  
 `pwzTypeName`  
 [in] Název <xref:System.Type> , který definuje metodu, který má být vyvolán.  
  
 `pwzMethodName`  
 [in] Název metody, která se má vyvolat.  
  
 `pwzArgument`  
 [in] Parametr řetězec předat metodě.  
  
 `pReturnValue`  
 [out] Celé číslo hodnoty vrácené volanou metodu.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`ExecuteInDefaultAppDomain` bylo úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Pokud metoda vrátí E_FAIL, seznam CRL už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Vyvolaná metoda musí mít následující podpis:  
  
```  
static int pwzMethodName (String pwzArgument)  
```  
  
 kde `pwzMethodName` představuje název volanou metodu a `pwzArgument` představuje řetězcová hodnota předaná této metodě jako parametr. Pokud hodnota HRESULT je nastavena na hodnotu S_OK, `pReturnValue` je nastavena na celočíselnou hodnotu vrácenou příkazem volanou metodu. V opačném případě `pReturnValue` není nastaven.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
