---
title: ICorRuntimeHost::Stop – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1aea8cb4c180477fdd763a8af2f251db2d37d066
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorruntimehoststop-method"></a>ICorRuntimeHost::Stop – metoda
Zastaví spuštění kódu v modulu runtime pro aktuální proces.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Operace byla úspěšná.|  
|S_FALSE|Operaci se nepodařilo dokončit.|  
|E_FAIL|Došlo k neznámé, závažnou chybu. Pokud metoda vrátí E_FAIL, modul CLR (CLR) již není použitelné v procesu. Následující volání žádné hostování rozhraní API vrací HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
  
## <a name="remarks"></a>Poznámky  
 Není obvykle nutné volat `Stop` metoda, protože kód zastaví provádění při ukončení procesu.  
  
> [!NOTE]
>  Po volání `Stop`, modul CLR nelze znovu inicializovat do stejného procesu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Viz také  
 [ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
