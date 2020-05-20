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
ms.openlocfilehash: aae03b0dc76639c50f4615d41eef73990226b5f7
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442121"
---
# <a name="idebugautoattachautoattach-method"></a>IDebugAutoAttach::AutoAttach – metoda
Provede automatické připojování ladicího programu vyvolaného serverem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 pro Vždy nastavte na `GUID_NULL` .  
  
 `dwPid`  
 pro ID procesu, obvykle načteno pomocí `GetCurrentProcessId` funkce.  
  
 `dwProgramType`  
 pro Typ programu: `AUTOATTACH_PROGRAM_WIN32` , `AUTOATTACH_PROGRAM_COMPLUS` , nebo `AUTOATTACH_PROGRAM_UNKNOWN` .  
  
 `dwProgramId`  
 pro ID programu  
  
 `pszSessionId`  
 pro Řetězec předaný příkazem ladění  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, zda je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** DbgAutoAttach. h  
  
## <a name="see-also"></a>Viz také

- [IDebugAutoAttach – rozhraní](idebugautoattach-interface.md)
