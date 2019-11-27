---
title: INotifySource2::SetNotifyFilter – metoda
ms.date: 03/30/2017
api_name:
- INotifySource2.SetNotifyFilter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySource2::SetNotifyFilter
helpviewer_keywords:
- INotifySource2::SetNotifyFilter method [.NET Framework debugging]
- SetNotifyFilter method [.NET Framework debugging]
ms.assetid: 6351fc92-b126-4af6-9bf3-0a8ce92845fc
topic_type:
- apiref
ms.openlocfilehash: 554756bdda6e7167b013e7114e647f952cd1069d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435953"
---
# <a name="inotifysource2setnotifyfilter-method"></a>INotifySource2::SetNotifyFilter – metoda
Přiřadí filtr oznámení pro použití s tímto zdrojem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `in_NotifyFilter`  
 pro Bitová kombinace hodnot výčtu [NOTIFY_FILTER](../../../../docs/framework/unmanaged-api/diagnostics/notify-filter-enumeration.md) , které identifikují zpětná volání pro rozhraní API ladicího programu.  
  
 `in_pUserThreadFilter`  
 pro Ukazatel na strukturu [USER_THREAD](../../../../docs/framework/unmanaged-api/diagnostics/user-thread-structure.md) , která identifikuje vlákna pro rozhraní API ladicího programu.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, zda je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Viz také:

- [INotifySource2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [INotifyConnection2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [INotifySink2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
