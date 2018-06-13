---
title: ICLRDebugManager::EndConnection – metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.EndConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c58ce0389c77b6534cbbf37fe985f89c187065df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435822"
---
# <a name="iclrdebugmanagerendconnection-method"></a>ICLRDebugManager::EndConnection – metoda
Odebere přidružení mezi seznamu úloh a identifikátor a popisný název.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwConnectionId`  
 [v] Identifikátor specifický pro hostitele pro připojení a přidružené seznamu běžných úloh language runtime (CLR).  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`EndConnection` úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|[Beginconnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) se nikdy volat pomocí `dwConnectionId`, nebo `dwConnectionId` byl nula.|  
  
## <a name="remarks"></a>Poznámky  
 [Iclrdebugmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) poskytuje tři metody `BeginConnection`, [setconnectiontasks –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), a `EndConnection`, pro přidružení s identifikátory a popisné názvy seznam úloh.  
  
> [!IMPORTANT]
>  Tyto tři metody musí být voláno v určitém pořadí pro jednotlivé skupiny úloh. `BeginConnection` je volána nejprve vytvořit nové připojení. `SetConnectionTasks` je volána vedle zajistit sadu úloh, který se má přidružit toto připojení. `EndConnection` je volána poslední k odstranění přidružení mezi seznamu úloh a identifikátor a popisný název. Však mohou být vnořené volání pro různá připojení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [ICLRDebugManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [BeginConnection – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)  
 [SetConnectionTasks – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)  
 [IHostControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
