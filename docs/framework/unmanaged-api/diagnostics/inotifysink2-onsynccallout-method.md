---
title: INotifySink2::OnSyncCallOut – metoda
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallOut
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type:
- apiref
ms.openlocfilehash: ce0e192a9d7d5abf56a55f844cf886c386f1c563
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441991"
---
# <a name="inotifysink2onsynccallout-method"></a>INotifySink2::OnSyncCallOut – metoda
Vyvolá se, když je volání ven.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `in_CallID`  
 pro ID volání, které je mimo. Viz [struktura CALL_ID](call-id-structure.md).  
  
 `out_ppBuffer`  
 mimo Vyrovnávací paměť volání.  
  
 `out_pBufferSize`  
 mimo Velikost vyrovnávací paměti volání (v bajtech).  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, zda je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Viz také

- [INotifySink2 – rozhraní](inotifysink2-interface.md)
- [INotifySource2 – rozhraní](inotifysource2-interface.md)
- [INotifyConnection2 – rozhraní](inotifyconnection2-interface.md)
