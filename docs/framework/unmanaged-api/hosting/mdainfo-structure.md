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
ms.openlocfilehash: 517e0ae7fb5d5151f94f82d9146ebbf40bad2ef9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503858"
---
# <a name="mdainfo-structure"></a>MDAInfo – struktura
Poskytuje podrobnosti o `Event_MDAFired` události, které aktivují vytváření pomocníka spravovaného ladění (MDA).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
|------------|-----------------|  
|`lpMDACaption`|Název aktuální aplikace MDA Nadpis popisuje druh selhání, který spustil `Event_MDAFired` událost.|  
|`lpMDAMessage`|Výstupní zpráva poskytnutá aktuálním modulem MDA.|  
  
## <a name="remarks"></a>Poznámky  
 Asistenti spravovaného ladění (MDA) jsou pomocné pomůcky, které fungují ve spojení s modulem CLR (Common Language Runtime) k provádění úloh, jako je určení neplatných podmínek v modulu provádění modulu runtime nebo výpisu dalších informací o stavu modulu. MDA vygeneruje zprávy XML o událostech, které jsou jinak obtížné depeše. Jsou zvláště užitečné pro ladění přechodů mezi spravovaným a nespravovaným kódem.  
  
 Modul runtime provede následující kroky, pokud je vyvolána událost, která spustí vytvoření objektu MDA:  
  
- Pokud hostitel nezaregistroval instanci [IActionOnCLREvent –](iactiononclrevent-interface.md) voláním [ICLROnEventManager:: RegisterActionOnEvent –](iclroneventmanager-registeractiononevent-method.md) , aby mohl být upozorněn na `Event_MDAFired` událost, modul runtime pokračuje s výchozím chováním, které nehostuje.  
  
- Pokud hostitel zaregistroval obslužnou rutinu pro tuto událost, modul runtime zkontroluje, zda je k procesu připojen ladicí program. V takovém případě je modul runtime rozdělen do ladicího programu. V případě, že ladicí program pokračuje, volá do hostitele. Pokud není připojen ladicí program, modul runtime zavolá `IActionOnCLREvent::OnEvent` a předá ukazatel na `MDAInfo` instanci jako `data` parametr.  
  
 Hostitel se může rozhodnout aktivovat MDA a upozornit na aktivaci služby MDA. Díky tomu může hostitel příležitost přepsat výchozí chování a přerušit spravované vlákno, které událost vyvolalo, aby nedošlo k poškození stavu procesu. Další informace o použití MDA najdete v tématu [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. idl  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro hostování](hosting-structures.md)
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
