---
title: ICorDebugMDA::GetXML – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetXML
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type:
- apiref
ms.openlocfilehash: 219aa27296dffa525bf3e2b836825437a8ce77b0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207660"
---
# <a name="icordebugmdagetxml-method"></a>ICorDebugMDA::GetXML – metoda
Získá úplný datový proud XML přidružený k Pomocníkovi spravovaného ladění (MDA) reprezentovanému pomocí [ICorDebugMDA](icordebugmda-interface.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetXML (  
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
 mimo Ukazatel na délku datového proudu XML.  
  
 `szName`  
 mimo Pole, do kterého se má uložit datový proud XML. Pole může být prázdné.  
  
## <a name="remarks"></a>Poznámky  
 `GetXML`Metoda může ovlivnit výkon v závislosti na velikosti přidruženého datového proudu XML.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugMDA – rozhraní](icordebugmda-interface.md)
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
