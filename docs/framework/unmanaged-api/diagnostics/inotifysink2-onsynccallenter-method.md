---
title: INotifySink2::OnSyncCallEnter – metoda
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallEnter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallEnter
helpviewer_keywords:
- INotifySink2::OnSyncCallEnter method [.NET Framework debugging]
- OnSyncCallEnter method [.NET Framework debugging]
ms.assetid: e33265be-c25d-4145-ad02-c3e89d6f26c1
topic_type:
- apiref
ms.openlocfilehash: 85f00698f42f120b209cca14f293a58ae4c65f6f
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442030"
---
# <a name="inotifysink2onsynccallenter-method"></a>INotifySink2::OnSyncCallEnter – metoda
Vyvolá se při vstupu volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OnSyncCallEnter  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `in_CallID`  
 pro ID zadaného volání. Viz [struktura CALL_ID](call-id-structure.md).  
  
 `in_pBuffer`  
 pro Vyrovnávací paměť volání.  
  
 `in_BufferSize`  
 pro Velikost vyrovnávací paměti volání (v bajtech).  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, zda je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Viz také

- [INotifySink2 – rozhraní](inotifysink2-interface.md)
- [INotifySource2 – rozhraní](inotifysource2-interface.md)
- [INotifyConnection2 – rozhraní](inotifyconnection2-interface.md)
