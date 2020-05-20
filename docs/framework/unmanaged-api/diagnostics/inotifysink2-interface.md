---
title: INotifySink2 – rozhraní
ms.date: 03/30/2017
api_name:
- INotifySink2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2
helpviewer_keywords:
- INotifySink2 interface [.NET Framework debugging]
ms.assetid: c1018789-4206-455d-aacc-2d876fc0d0bb
topic_type:
- apiref
ms.openlocfilehash: c7afe074afb9b38d6fefa1192799120dbb50b403
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442056"
---
# <a name="inotifysink2-interface"></a>INotifySink2 – rozhraní
Deklaruje metody pro oznámení jímky.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[OnSyncCallEnter – metoda](inotifysink2-onsynccallenter-method.md)|Vyvolá se při vstupu volání.|  
|[OnSyncCallExit – metoda](inotifysink2-onsynccallexit-method.md)|Vyvolá se při ukončení volání.|  
|[OnSyncCallOut – metoda](inotifysink2-onsynccallout-method.md)|Vyvolá se, když je volání ven.|  
|[OnSyncCallReturn – metoda](inotifysink2-onsynccallreturn-method.md)|Vyvolá se, když se volání vrátí.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Viz také

- [INotifyConnection2 – rozhraní](inotifyconnection2-interface.md)
- [INotifySource2 – rozhraní](inotifysource2-interface.md)
- [Rozhraní úložiště symbolů diagnostiky](diagnostics-symbol-store-interfaces.md)
