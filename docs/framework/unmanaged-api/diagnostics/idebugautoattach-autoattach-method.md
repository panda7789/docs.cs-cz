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
ms.openlocfilehash: 5064e66708044d82e3a097c8235b5b28a3412200
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986489"
---
# <a name="idebugautoattachautoattach-method"></a>IDebugAutoAttach::AutoAttach – metoda
Provede automaticky serveru vyvolá ladicí program připojit.  
  
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
  
## <a name="parameters"></a>Parametry  
 `guidPort`  
 [in] Vždy nastaven na hodnotu `GUID_NULL`.  
  
 `dwPid`  
 [in] ID, obvykle načteno pomocí procesu `GetCurrentProcessId` funkce.  
  
 `dwProgramType`  
 [in] Typ programu: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, nebo `AUTOATTACH_PROGRAM_UNKNOWN`.  
  
 `dwProgramId`  
 [in] ID programu.  
  
 `pszSessionId`  
 [in] Řetězec předaný příkaz debug.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda uspěje.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** DbgAutoAttach.h  
  
## <a name="see-also"></a>Viz také:

- [IDebugAutoAttach – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
