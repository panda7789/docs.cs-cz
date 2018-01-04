---
title: "INotifySource2::SetNotifyFilter – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifySource2.SetNotifyFilter
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifySource2::SetNotifyFilter
helpviewer_keywords:
- INotifySource2::SetNotifyFilter method [.NET Framework debugging]
- SetNotifyFilter method [.NET Framework debugging]
ms.assetid: 6351fc92-b126-4af6-9bf3-0a8ce92845fc
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bba34a9e28d1995ca04c7108ce33adc6e676b357
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="inotifysource2setnotifyfilter-method"></a>INotifySource2::SetNotifyFilter – metoda
Přiřadí filtr oznámení pro použití s tímto zdrojem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `in_NotifyFilter`  
 [v] Bitové kombinace [NOTIFY_FILTER](../../../../docs/framework/unmanaged-api/diagnostics/notify-filter-enumeration.md) hodnot výčtu, které identifikují zpětná volání rozhraní API v ladicím programu.  
  
 `in_pUserThreadFilter`  
 [v] Ukazatel [user_thread –](../../../../docs/framework/unmanaged-api/diagnostics/user-thread-structure.md) struktura, která identifikuje vláken v ladicím programu rozhraní API.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda bude úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Viz také  
 [INotifySource2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [INotifyConnection2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 [INotifySink2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
