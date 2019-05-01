---
title: IHostIoCompletionManager::Bind – metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.Bind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::Bind
helpviewer_keywords:
- IHostIoCompletionManager::Bind method [.NET Framework hosting]
- Bind method [.NET Framework hosting]
ms.assetid: acd74cb5-7e22-4a07-83c3-82288e1abd9f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fa87026e0d4c93da782be15bef98afa9a0e4dfd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984357"
---
# <a name="ihostiocompletionmanagerbind-method"></a>IHostIoCompletionManager::Bind – metoda
Vytvoří vazbu určený port dokončení vstupně-výstupních operací, který byl vytvořen v dřívějším volání [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `hPort`  
 [in] Port dokončení vstupně-výstupních operací, ke kterému se vytvořit vazbu `hHandle`. Pokud hodnota `hPort` má hodnotu null, `hHandle` je vázán na výchozí port dokončení vstupně-výstupních operací.  
  
 `hHandle`  
 [in] Popisovač operačního systému vytvořit vazbu na `hPort`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`Bind` bylo úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Port dokončení vstupně-výstupních operací je vytvořena pomocí volání `CreateIoCompletionPort`. Volání CLR `Bind` svázat popisovač na daný port.  
  
> [!NOTE]
>  Po dokončení se požadavek na vstupně-výstupních operací, musí volat hostitele [iclriocompletionmanager::onComplete –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRIoCompletionManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
