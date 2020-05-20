---
title: INotifyConnection2::RegisterNotifySource – metoda
ms.date: 03/30/2017
api_name:
- INotifyConnection2.RegisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type:
- apiref
ms.openlocfilehash: b7fa777466e2c7edd7b3110dd91e776785c63c58
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442069"
---
# <a name="inotifyconnection2registernotifysource-method"></a>INotifyConnection2::RegisterNotifySource – metoda
Nainstaluje zadaný zdroj oznámení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `in_pNotifySource`  
 pro Určuje objekt, který má být použit jako zdroj oznámení.  
  
 `out_ppNotifySink`  
 mimo Přijme objekt, který se má použít jako jímka oznámení.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, zda je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Viz také

- [INotifyConnection2 – rozhraní](inotifyconnection2-interface.md)
- [INotifySource2 – rozhraní](inotifysource2-interface.md)
- [INotifySink2 – rozhraní](inotifysink2-interface.md)
- [UnregisterNotifySource – metoda](inotifyconnection2-unregisternotifysource-method.md)
