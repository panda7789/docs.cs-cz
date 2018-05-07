---
title: IDebugAutoAttach::AutoAttach – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5c95423a6918da7cc043f8d46de13d166b8d895
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
