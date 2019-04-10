---
title: ICLRDebugManager::SetConnectionTasks – metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetConnectionTasks
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88078fa34910dca642eae3cf261c9e00fae4f27a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201985"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a>ICLRDebugManager::SetConnectionTasks – metoda
Přidruží seznam [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance s identifikátorem a popisný název.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `id`  
 [in] Identifikátor konkrétního hostitele pro připojení ke které chcete přidružit `ppCLRTask` pole.  
  
 `dwCount`  
 [in] Počet členů `ppCLRTask`. Tato hodnota musí být větší než nula.  
  
 `ppCLRTask`  
 [in] Pole `ICLRTask` ukazatele pro přidružení k připojení identifikovaný `id`. Toto pole musí obsahovat alespoň jeden člen.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`SetConnectionTasks` bylo úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|[Beginconnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) nebyla volána pomocí této hodnoty `id`, nebo `dwCount` nebo `id` se žádný nebo jeden z prvků `ppCLRTask` má hodnotu null.|  
  
## <a name="remarks"></a>Poznámky  
 [Iclrdebugmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) poskytuje tři metody `BeginConnection`, `SetConnectionTasks`, a [endconnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), pro seznamy úloh přidružení s identifikátory a popisné názvy.  
  
> [!IMPORTANT]
>  Tyto tři metody musí být volána v určitém pořadí pro každou sadu úkolů. `BeginConnection` je volána nejprve vytvořit nové připojení. `SetConnectionTasks` je volána dále k poskytování sadu úloh, který se má přidružit toto připojení. `EndConnection` Chcete-li odebrat přidružení seznamu úkolů a identifikátor a popisný název se nazývá poslední. Volání pro různá připojení však mohou být vnořené.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRDebugManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [BeginConnection – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [EndConnection – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [IHostControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
