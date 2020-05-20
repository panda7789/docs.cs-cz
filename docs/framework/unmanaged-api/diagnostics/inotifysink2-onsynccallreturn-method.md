---
title: INotifySink2::OnSyncCallReturn – metoda
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallReturn
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallReturn
helpviewer_keywords:
- OnSyncCallReturn method [.NET Framework debugging]
- INotifySink2::OnSyncCallReturn method [.NET Framework debugging]
ms.assetid: c1bda761-6292-4750-a14b-7d5db8f33456
topic_type:
- apiref
ms.openlocfilehash: ff1dabcfc366607639cd98be4392f8dd59dc83a1
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442004"
---
# <a name="inotifysink2onsynccallreturn-method"></a>INotifySink2::OnSyncCallReturn – metoda
Vyvolá se, když se volání vrátí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `in_CallID`  
 pro ID volání, ze kterého se vrací. Viz [struktura CALL_ID](call-id-structure.md).  
  
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
