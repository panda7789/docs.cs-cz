---
title: ICorDebugMDA::GetName – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetName
helpviewer_keywords:
- ICorDebugMDA::GetName method [.NET Framework debugging]
- GetName method, ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 885bf5e8-00b7-4cd7-9d8d-e720d47918c4
topic_type:
- apiref
ms.openlocfilehash: 6a6769265a2e140f1fa001bb8240bc5d4bd76018
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213670"
---
# <a name="icordebugmdagetname-method"></a>ICorDebugMDA::GetName – metoda
Získá řetězec obsahující název pomocníka spravovaného ladění (MDA) reprezentovaný [ICorDebugMDA](icordebugmda-interface.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cchName`  
 pro Velikost `szName` pole.  
  
 `pcchName`  
 mimo Ukazatel na délku názvu.  
  
 `szName`  
 mimo Pole, do kterého se má uložit název  
  
## <a name="remarks"></a>Poznámky  
 Názvy MDA jsou jedinečné hodnoty. `GetName`Metoda je pohodlný alternativní výkon pro získání datového proudu XML a extrakci názvu z datového proudu založeného na schématu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugMDA – rozhraní](icordebugmda-interface.md)
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
