---
title: ICorDebugRegisterSet2::GetRegisters – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aca83a66520531074f376a47a7f2994cda237f9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugregisterset2getregisters-method"></a>ICorDebugRegisterSet2::GetRegisters – metoda
Získá hodnotu každý registrace (pro platformu, na kterém je aktuálně provádění kódu), který je určen podle dané bit masky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `maskCount`  
 [v] Velikost v bajtech z `mask` pole.  
  
 `mask`  
 [v] Pole bajtů, každý bit odpovídá registraci. Pokud je bit 1, budou načteny odpovídající registrace hodnotu.  
  
 `regCount`  
 [v] Počet hodnot registru, které mají být načteny.  
  
 `regBuffer`  
 [out] Pole `CORDB_REGISTER` objekty, z nichž každý obdrží hodnotu registru.  
  
## <a name="remarks"></a>Poznámky  
 `GetRegisters` Metoda vrátí pole hodnot z registrů, které jsou určené maska. Pole neobsahuje hodnoty registrů, jejichž bit masky není nastavený. Proto velikost `regBuffer` pole musí být stejný jako počet na 1 v masce. Pokud hodnota `regCount` je příliš malá pro počet registry indikován maska hodnoty vyšší číslem registrů bude zkrácen ze sady. Pokud `regCount` je příliš velký, nepoužívané `regBuffer` elementy bude beze změny.  
  
 Pokud není k dispozici registrace je indikován maska, neurčitém hodnotu, bude vrácen pro této registrace.  
  
 `ICorDebugRegisterSet2::GetRegisters` Metoda je nezbytné pro platformy, které mají víc než 64 Registry. IA64 má například 128 registry obecné účely a 128 zaregistruje se s plovoucí desetinnou čárkou, proto musíte víc než 64 bitů v bitová maska.  
  
 Pokud nemáte víc než 64 registrů, stejně jako v případě na platformách, například x86, `GetRegisters` metoda ve skutečnosti jenom překládá bajtů v `mask` do bajtového pole `ULONG64` a potom zavolá [ICorDebugRegisterSet:: Getregisters –](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) metoda, která přebírá `ULONG64` masky.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugRegisterSet2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [ICorDebugRegisterSet – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
