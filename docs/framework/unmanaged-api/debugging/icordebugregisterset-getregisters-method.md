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
ms.openlocfilehash: 32e899622b9c649a08e3bca1b6645f70dcbcbb19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178535"
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters – metoda
Získá hodnotu každého registru (v počítači, který je aktuálně spuštěn kód), který je určen bitovou maskou.  
  
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
 [v] Bitová maska, která určuje, které hodnoty registru mají být načteny. Každý bit odpovídá registru. Pokud bit je nastavena na jeden, hodnota registru je načten; v opačném případě není načtena hodnota registru.  
  
 `regCount`  
 [v] Počet hodnot registru, které mají být načteny.  
  
 `regBuffer`  
 [out] Pole `CORDB_REGISTER` objektů, z nichž každý obdrží hodnotu registru.  
  
## <a name="remarks"></a>Poznámky  
 Velikost pole by měla být rovna počtu bitů nastavených na jeden v bitové masce. Parametr `regCount` určuje počet prvků ve vyrovnávací paměti, které obdrží hodnoty registru. Pokud `regCount` je hodnota příliš malá pro počet registrů označených maskou, vyšší číslované registry budou ze sady zkráceny. Pokud `regCount` je hodnota příliš velká, `regBuffer` nepoužívané prvky budou nezměněny.  
  
 Pokud bitová maska určuje registr, `GetRegisters` který není k dispozici, vrátí pro tento registr neurčitou hodnotu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugRegisterSet – rozhraní](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 – rozhraní](icordebugregisterset2-interface.md)
