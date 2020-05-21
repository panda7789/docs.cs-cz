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
ms.openlocfilehash: 15004238ee296e44ae77cd8739b7f62ea2a7a100
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762965"
---
# <a name="iclrtaskreset-method"></a>ICLRTask::Reset – metoda
Informuje modul CLR (Common Language Runtime), který hostitel dokončil úlohu, a umožňuje, aby CLR znovu používá aktuální instanci [ICLRTask](iclrtask-interface.md) k tomu, aby reprezentovala jinou úlohu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fFull`  
 [in] `true` , pokud by měl modul runtime kromě informací o zabezpečení a národním prostředí v souvislosti s aktuální instancí obnovit všechny statické hodnoty související s vlákny. v `ICLRTask` opačném případě `false` .  
  
 Pokud je hodnota `true` , modul runtime resetuje data uložená pomocí <xref:System.Threading.Thread.AllocateDataSlot%2A> nebo <xref:System.Threading.Thread.AllocateNamedDataSlot%2A> .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`Reset`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo zpracovat volání. Nepodařilo|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR může recyklovat dříve vytvořené `ICLRTask` instance, aby nedocházelo k režii opakovaného vytváření nových instancí pokaždé, když potřebuje nový úkol. Hostitel tuto funkci povolí voláním `ICLRTask::Reset` namísto [ICLRTask:: ExitTask –](iclrtask-exittask-method.md) při dokončení úlohy. Následující seznam shrnuje normální životní cyklus `ICLRTask` instance:  
  
1. Modul runtime vytvoří novou `ICLRTask` instanci.  
  
2. Běhové volání [IHostTaskManager:: GetCurrentTask –](ihosttaskmanager-getcurrenttask-method.md) získá odkaz na aktuální úlohu hostitele.  
  
3. Běhové volání [IHostTask:: SetCLRTask –](ihosttask-setclrtask-method.md) přiřadí novou instanci k úloze hostitele.  
  
4. Úloha se spustí a dokončí.  
  
5. Hostitel zničí úlohu voláním `ICLRTask::ExitTask` .  
  
 `Reset`mění tento scénář dvěma způsoby. V kroku 5 výše Hostitel volá `Reset` pro resetování úlohy do čistého stavu a potom oddělí `ICLRTask` instanci od přidružené instance [IHostTask](ihosttask-interface.md) . V případě potřeby může hostitel také `IHostTask` instanci pro opakované použití ukládat do mezipaměti. V kroku 1 výše si modul runtime z mezipaměti vyžádá recyklaci, `ICLRTask` místo aby se vytvořila nová instance.  
  
 Tento přístup funguje i v případě, že hostitel má také fond opakovaně použitelných pracovních úloh. Když hostitel zničí jednu z jeho `IHostTask` instancí, zničí odpovídající `ICLRTask` volání `ExitTask` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRTask – rozhraní](iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](ihosttask-interface.md)
- [IHostTaskManager – rozhraní](ihosttaskmanager-interface.md)
