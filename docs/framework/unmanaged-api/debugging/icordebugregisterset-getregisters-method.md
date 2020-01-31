---
title: ICorDebugRegisterSet::GetRegisters – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
ms.openlocfilehash: 737993ac80b26d490915af3e97fd6a9552246aee
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792109"
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters – metoda
Získá hodnotu každého registru (na počítači, který právě spouští kód), který je určen bitovou maskou.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mask`  
 pro Bitová maska, která určuje, které hodnoty registru mají být načteny. Každý bit odpovídá registru. Pokud je bit nastavený na jeden, načte se hodnota registru. v opačném případě se hodnota registru nenačte.  
  
 `regCount`  
 pro Počet hodnot registru, které mají být načteny.  
  
 `regBuffer`  
 mimo Pole objektů `CORDB_REGISTER`, z nichž každý přijímá hodnotu registru.  
  
## <a name="remarks"></a>Poznámky  
 Velikost pole musí být rovna počtu bitů nastaveným na jednu v bitové masce. Parametr `regCount` určuje počet prvků ve vyrovnávací paměti, které budou přijímat hodnoty registru. Pokud je hodnota `regCount` příliš malá pro počet registrů, které jsou označeny maskou, budou z množiny zkráceny i tyto registry s vyšším číslem. Pokud je hodnota `regCount` příliš velká, nepoužívané prvky `regBuffer` nebudou změněny.  
  
 Pokud Bitová maska určuje registr, který není k dispozici, `GetRegisters` vrátí neurčitou hodnotu pro tento registr.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugRegisterSet – rozhraní](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 – rozhraní](icordebugregisterset2-interface.md)
