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
ms.openlocfilehash: e2dc1064656f3493db78d858cf1e86db0cb83d6c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136692"
---
# <a name="icordebugregisterset2getregisters-method"></a>ICorDebugRegisterSet2::GetRegisters – metoda
Získá hodnotu každý registr (pro platformu, na kterém právě spouští kód), který je určen podle daného bitové masky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `maskCount`  
 [in] Velikost v bajtech, nástroje `mask` pole.  
  
 `mask`  
 [in] Pole bajtů, každý bit odpovídá registru. Pokud bit na hodnotu 1, budou načteny hodnoty odpovídající registru.  
  
 `regCount`  
 [in] Počet hodnot registru, který se má načíst.  
  
 `regBuffer`  
 [out] Pole `CORDB_REGISTER` objektů, z nichž každý přijímá hodnotu z registru.  
  
## <a name="remarks"></a>Poznámky  
 `GetRegisters` Metoda vrátí pole hodnot z registrů, která jsou určena pomocí masky. Pole neobsahuje hodnoty registrů, jejichž bitová maska není nastavena. Díky tomu se velikost `regBuffer` pole musí být stejná jako číslo od 1 masce. Pokud hodnota `regCount` je příliš malá pro počet registrů indikován maska hodnoty vyšší číslované registrů se zkrátí ze sady. Pokud `regCount` je příliš velká, nepoužívané `regBuffer` prvky bude bez úprav.  
  
 Pokud není k dispozici registr je indikován maska, vrátí se neurčitá hodnota pro tento registr.  
  
 `ICorDebugRegisterSet2::GetRegisters` Metoda je nezbytná pro platformy, které mají více než 64 registrů. IA64 má například 128 registrů pro obecné účely a zaregistruje se 128 s plovoucí desetinnou čárkou, tak budete potřebovat víc než 64 bitů v bitové masce.  
  
 Pokud nemáte více než 64 registrů, stejně jako v případě na platformách, například x86, `GetRegisters` metoda ve skutečnosti právě přeloží bajtů v `mask` do bajtového pole `ULONG64` a pak zavolá [icordebugregisterset –:: Getregisters –](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) metoda, která přijímá `ULONG64` masky.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugRegisterSet2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
