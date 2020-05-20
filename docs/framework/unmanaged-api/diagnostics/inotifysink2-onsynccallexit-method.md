---
title: INotifySink2::OnSyncCallExit – metoda
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallExit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallExit
helpviewer_keywords:
- INotifySink2::OnSyncCallExit method [.NET Framework debugging]
- OnSyncCallExit method [.NET Framework debugging]
ms.assetid: d9d7600e-a8f5-443a-96de-67d26e130f2d
topic_type:
- apiref
ms.openlocfilehash: f81ef3f5959e279b3fbbd94d6c5e8a2d86a38e7f
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442017"
---
# <a name="inotifysink2onsynccallexit-method"></a>INotifySink2::OnSyncCallExit – metoda
Vyvolá se při ukončení volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OnSyncCallExit  
(  
    [in]  CALL_ID   in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*    out_pBufferSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `in_CallID`  
 pro ID volání, které se ukončilo. Viz [struktura CALL_ID](call-id-structure.md).  
  
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
