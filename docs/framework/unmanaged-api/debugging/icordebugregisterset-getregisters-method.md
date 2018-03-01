---
title: "ICorDebugRegisterSet::GetRegisters – metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ddefb1ac5694bf1f213dd77e0ffc7f746b7e62cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters – metoda
Získá hodnotu každý registrace (v počítači, který je aktuálně provádění kódu), který je určen podle bit masky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mask`  
 [v] Bitová maska, která určuje registrace, které se mají načíst hodnoty. Každý bit odpovídá registraci. Pokud je trochu nastaven na jednu, je načíst hodnoty registru; jinak není načíst hodnoty registru.  
  
 `regCount`  
 [v] Počet hodnot registru, které mají být načteny.  
  
 `regBuffer`  
 [out] Pole `CORDB_REGISTER` objekty, z nichž každý obdrží hodnotu registru.  
  
## <a name="remarks"></a>Poznámky  
 Velikost pole musí být roven počtu bitů, které jsou nastavené na jednu v bitová maska. `regCount` Parametr určuje počet elementů ve vyrovnávací paměti, která bude přijímat hodnot registru. Pokud `regCount` hodnota je příliš malý počet registry indikován maska, vyšší číslem registry bude zkrácen ze sady. Pokud `regCount` hodnota je příliš velký, nepoužívané `regBuffer` elementy bude beze změny.  
  
 Pokud bitová maska určuje registrace, který je k dispozici, `GetRegisters` vrací neurčitém hodnotu pro tento registrace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugRegisterSet – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [ICorDebugRegisterSet2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
