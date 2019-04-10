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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9144ab7fc74bdb5b980b4ff1e1a903653bd056f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216272"
---
# <a name="inotifysink2onsynccallexit-method"></a>INotifySink2::OnSyncCallExit – metoda
Získá vyvolána při ukončení volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnSyncCallExit  
(  
    [in]  CALL_ID   in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*    out_pBufferSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `in_CallID`  
 [in] ID volání se ukončil. Zobrazit [call_id – struktura](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).  
  
 `out_ppBuffer`  
 [out] Volání vyrovnávací paměti.  
  
 `out_pBufferSize`  
 [out] Velikost vyrovnávací paměti volání, v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda uspěje.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Viz také:

- [INotifySink2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [INotifySource2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [INotifyConnection2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
