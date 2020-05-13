---
title: ICorDebugFunction::GetCurrentVersionNumber – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetCurrentVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type:
- apiref
ms.openlocfilehash: b47580022b98ea02584a94b3f74b3fd1c276f297
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212903"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a>ICorDebugFunction::GetCurrentVersionNumber – metoda
Získá číslo verze nejnovější úpravy provedené na funkci reprezentované tímto objektem ICorDebugFunction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pnCurrentVersion`  
 mimo Ukazatel na celočíselnou hodnotu, která je číslo verze poslední úpravy provedené u této funkce.  
  
## <a name="remarks"></a>Poznámky  
 Číslo verze nejnovější úpravy provedené v této funkci může být větší než číslo verze samotné funkce. Pomocí metody [ICorDebugFunction2:: getčíslo_verze](icordebugfunction2-getversionnumber-method.md) nebo [ICorDebugCode:: getčíslo_verze](icordebugcode-getversionnumber-method.md) načtěte číslo verze funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
