---
title: MDAInfo – struktura
ms.date: 03/30/2017
api_name:
- MDAInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MDAInfo
helpviewer_keywords:
- MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type:
- apiref
ms.openlocfilehash: 9a2f513d40d722f1b0aad823ac7c0d93bda5615f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123262"
---
# <a name="mdainfo-structure"></a>MDAInfo – struktura
Poskytuje podrobnosti o události `Event_MDAFired`, která aktivuje vytvoření pomocníka spravovaného ladění (MDA).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`lpMDACaption`|Název aktuální aplikace MDA Nadpis popisuje druh selhání, které aktivovalo událost `Event_MDAFired`.|  
|`lpMDAMessage`|Výstupní zpráva poskytnutá aktuálním modulem MDA.|  
  
## <a name="remarks"></a>Poznámky  
 Asistenti spravovaného ladění (MDA) jsou pomocné pomůcky, které fungují ve spojení s modulem CLR (Common Language Runtime) k provádění úloh, jako je určení neplatných podmínek v modulu provádění modulu runtime nebo výpisu dalších informací o stavu jádra. MDA vygeneruje zprávy XML o událostech, které jsou jinak obtížné depeše. Jsou zvláště užitečné pro ladění přechodů mezi spravovaným a nespravovaným kódem.  
  
 Modul runtime provede následující kroky, pokud je vyvolána událost, která spustí vytvoření objektu MDA:  
  
- Pokud hostitel nezaregistroval instanci [IActionOnCLREvent –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) voláním [ICLROnEventManager:: RegisterActionOnEvent –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) , aby mohl být upozorněn na událost `Event_MDAFired`, modul runtime pokračuje s výchozím chováním, který nehostuje.  
  
- Pokud hostitel zaregistroval obslužnou rutinu pro tuto událost, modul runtime zkontroluje, zda je k procesu připojen ladicí program. V takovém případě je modul runtime rozdělen do ladicího programu. V případě, že ladicí program pokračuje, volá do hostitele. Pokud není připojen žádný ladicí program, modul runtime zavolá `IActionOnCLREvent::OnEvent` a předá ukazatel na instanci `MDAInfo` jako parametr `data`.  
  
 Hostitel se může rozhodnout aktivovat MDA a upozornit na aktivaci služby MDA. Díky tomu může hostitel příležitost přepsat výchozí chování a přerušit spravované vlákno, které událost vyvolalo, aby nedošlo k poškození stavu procesu. Další informace o použití MDA najdete v tématu [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. idl  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
