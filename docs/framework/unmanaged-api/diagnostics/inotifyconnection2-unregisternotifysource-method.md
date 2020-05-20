---
title: INotifyConnection2::UnregisterNotifySource – metoda
ms.date: 03/30/2017
api_name:
- INotifyConnection2.UnregisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::UnregisterNotifySource
helpviewer_keywords:
- INotifyConnection2::UnregisterNotifySource method [.NET Framework debugging]
- UnregisterNotifySource method [.NET Framework debugging]
ms.assetid: 2fc6c715-646f-41fd-9c12-c59b40575269
topic_type:
- apiref
ms.openlocfilehash: 9d0fcdcd4fe1561f7565586e3327c6d3d7e0fe0a
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442043"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a>INotifyConnection2::UnregisterNotifySource – metoda
Odebere zadaný zdrojový objekt oznámení z připojení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `in_pNotifySource`  
 pro Odregistrování objektu oznámení  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, zda je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Viz také

- [INotifyConnection2 – rozhraní](inotifyconnection2-interface.md)
- [INotifySource2 – rozhraní](inotifysource2-interface.md)
- [INotifySink2 – rozhraní](inotifysink2-interface.md)
- [RegisterNotifySource – metoda](inotifyconnection2-registernotifysource-method.md)
