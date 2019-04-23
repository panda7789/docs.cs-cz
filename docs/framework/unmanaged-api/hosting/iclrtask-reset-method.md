---
title: ICLRTask::Reset – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13bf7342157de48e0183537afea2f2e53d1498dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300304"
---
# <a name="iclrtaskreset-method"></a>ICLRTask::Reset – metoda
Informuje o tom common language runtime (CLR), že byla dokončena úloha hostitele a umožňuje modulu CLR pro opětovné použití aktuální [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance k reprezentování jiného úkolu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fFull`  
 [in] `true`, pokud modul runtime by měl obnovit všechny statické hodnoty související vlákna plody kromě a informace o zabezpečení a národní prostředí aktuálního `ICLRTask` instance; v opačném případě `false`.  
  
 Pokud je hodnota `true`, modul runtime obnoví data, která byla uložena pomocí <xref:System.Threading.Thread.AllocateDataSlot%2A> nebo <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`Reset` bylo úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nemůže spouštět spravovaný kód a zpracovat volání. úspěšně|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR recykluje dříve vytvořili `ICLRTask` instancí, aby režijní náklady na opakované vytváření nové instance pokaždé, když potřebuje novou úlohu. Hostitele povolí tuto funkci voláním `ICLRTask::Reset` místo [iclrtask::exittask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) po jeho dokončení úkolu. Následující seznam shrnuje běžné životní cyklus `ICLRTask` instance:  
  
1. Vytvoří nový modul runtime `ICLRTask` instance.  
  
2. Modul runtime zavolá [ihosttaskmanager::getcurrenttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) získat odkaz na aktuální úlohu na hostiteli.  
  
3. Modul runtime zavolá [ihosttask::setclrtask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) přidružit nové instance hostitele úloh.  
  
4. Úloha spustí a dokončí.  
  
5. Hostitele odstraní úlohu voláním `ICLRTask::ExitTask`.  
  
 `Reset` upravuje tento scénář dvěma způsoby. V kroku 5 výše volání hostitele `Reset` resetovat úlohy do čistého stavu a potom odpojí `ICLRTask` instanci z jeho přidruženého [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance. V případě potřeby hostitele lze také ukládat do mezipaměti `IHostTask` instance pro opakované použití. V kroku 1 výše, modul runtime si vyžádá recyklovat `ICLRTask` z mezipaměti místo vytvoření nové instance.  
  
 Tento přístup funguje dobře, když se hostitel má také fondu úkolů opakovaně použitelného pracovního procesu. Když hostitel odstraní jeden z jeho `IHostTask` instancí, zlikvidují odpovídající `ICLRTask` voláním `ExitTask`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
