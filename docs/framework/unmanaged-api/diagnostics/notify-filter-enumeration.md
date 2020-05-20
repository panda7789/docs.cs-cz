---
title: NOTIFY_FILTER – výčet
ms.date: 03/30/2017
api_name:
- NOTIFY_FILTER
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- NOTIFY_FILTER
helpviewer_keywords:
- NOTIFY_FILTER enumeration [.NET Framework debugging]
ms.assetid: 4789d08f-8683-45d3-ac30-73d48c61e470
topic_type:
- apiref
ms.openlocfilehash: b20e18d5f4314a0ab1442ac7bd5c6514e4db85d5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609479"
---
# <a name="notify_filter-enumeration"></a>NOTIFY_FILTER – výčet
Označuje zpětná volání pro funkce ladicího programu. Další informace naleznete v tématu metoda [INotifySource2 –:: setnotifyfilter –](inotifysource2-setnotifyfilter-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum tagNOTIFY_FILTER  
{  
    NOTIFY_FILTER_ONSYNCCALLOUT    = 0x1,  
    NOTIFY_FILTER_ONSYNCCALLENTER  = 0x2,  
    NOTIFY_FILTER_ONSYNCCALLEXIT   = 0x4,  
    NOTIFY_FILTER_ONSYNCCALLRETURN = 0x8,  
    NOTIFY_FILTER_ALLSYNC = NOTIFY_FILTER_ONSYNCCALLOUT | NOTIFY_FILTER_ONSYNCCALLENTER | NOTIFY_FILTER_ONSYNCCALLEXIT | NOTIFY_FILTER_ONSYNCCALLRETURN,  
    NOTIFY_FILTER_ALL              = 0xffffffff,  
    NOTIFY_FILTER_NONE             = 0  
};  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|Označuje, že by měla být vyvolána metoda [INotifySink2:: onsynccallout –](inotifysink2-onsynccallout-method.md) .|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|Označuje, že by měla být vyvolána metoda [INotifySink2:: onsynccallenter –](inotifysink2-onsynccallenter-method.md) .|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|Označuje, že by měla být vyvolána metoda [INotifySink2:: onsynccallexit –](inotifysink2-onsynccallexit-method.md) .|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|Označuje, že by měla být vyvolána metoda [INotifySink2:: onsynccallreturn –](inotifysink2-onsynccallreturn-method.md) .|  
|`NOTIFY_FILTER_ALLSYNC`|Označuje, že by měly být vyvolány všechny metody [INotifySink2](inotifysink2-interface.md) .|  
|`NOTIFY_FILTER_ALL`|Aktivuje všechna existující a budoucí oznámení.|  
|`NOTIFY_FILTER_NONE`|Označuje, že by neměly být vyvolány žádné metody oznámení.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Viz také

- [Výčty úložiště symbolů diagnostiky](diagnostics-symbol-store-enumerations.md)
