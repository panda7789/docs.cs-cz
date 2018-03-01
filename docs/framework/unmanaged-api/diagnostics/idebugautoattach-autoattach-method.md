---
title: "IDebugAutoAttach::AutoAttach – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IDebugAutoAttach.AutoAttach
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3b875fec2fdb6ecaeaccf8e58030b2fccbb8653b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="idebugautoattachautoattach-method"></a>IDebugAutoAttach::AutoAttach – metoda
Provede server volá ladicí program automaticky připojit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidPort`  
 [v] Vždy nastaven na hodnotu `GUID_NULL`.  
  
 `dwPid`  
 [v] ID, obvykle načíst pomocí procesu `GetCurrentProcessId` funkce.  
  
 `dwProgramType`  
 [v] Program typu: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, nebo `AUTOATTACH_PROGRAM_UNKNOWN`.  
  
 `dwProgramId`  
 [v] ID programu.  
  
 `pszSessionId`  
 [v] Řetězec předaná příkaz debug.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda bude úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** DbgAutoAttach.h  
  
## <a name="see-also"></a>Viz také  
 [IDebugAutoAttach – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
