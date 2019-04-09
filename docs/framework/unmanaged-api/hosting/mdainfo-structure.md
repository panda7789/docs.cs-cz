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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3be6f2b9454ed2f74d2cc6792cd9aaa2c25215db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104608"
---
# <a name="mdainfo-structure"></a>MDAInfo – struktura
Poskytuje podrobnosti o `Event_MDAFired` událost, která se aktivuje vytvořením Pomocník spravovaného ladění (MDA).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`lpMDACaption`|Název aktuální MDA. Název popisuje typ selhání, které aktivuje `Event_MDAFired` událostí.|  
|`lpMDAMessage`|Výstupní zprávy poskytnuté aktuální MDA.|  
  
## <a name="remarks"></a>Poznámky  
 Asistentů spravovaného ladění (mda) jsou pomůcky, které fungují ve spojení s common language runtime (CLR) k provádění úloh, jako je identifikace neplatné podmínky pro ladění v prováděcí modul runtime nebo vypsání Další informace o stavu modul. Mda generování zpráv XML o událostech, které jsou jinak obtížné zachytit. Jsou obzvláště užitečné pro ladění přechody mezi spravovaným a nespravovaným kódem.  
  
 Modul runtime provede následující kroky, když se aktivuje událost, která se aktivuje vytvořením MDA:  
  
-   Pokud nebyla zaregistrována hostitele [iactiononclrevent –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance voláním [iclroneventmanager::registeractiononevent –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) upozornit `Event_MDAFired` události, modul runtime bude pokračovat jeho výchozí chování bez hostitele.  
  
-   Pokud hostitel je zaregistrovaná obslužná rutina pro tuto událost, zkontroluje modulu runtime, zda je připojen ladicí program k procesu. Pokud se jedná, modul runtime se dělí do ladicího programu. Pokud ladicí program bude pokračovat, volá do hostitele. Pokud je připojen ladicí program nebyl, modul runtime zavolá `IActionOnCLREvent::OnEvent` a předává ukazatel `MDAInfo` instance jako `data` parametr.  
  
 K aktivaci mda a která vás upozorní, když MDA aktivováno, můžete zvolit hostitele. To dává možnost přepsat výchozí chování a na spravovaná vlákna, která vyvolala událost, chcete-li zabránit poškození stav procesu zrušení hostitele. Další informace o používání mda najdete v tématu [diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.idl  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
