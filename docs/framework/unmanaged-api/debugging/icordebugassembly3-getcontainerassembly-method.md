---
title: ICorDebugAssembly3::GetContainerAssembly – metoda
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acb34ac2568ac88797441306820e6e762b5ac46e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409724"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a>ICorDebugAssembly3::GetContainerAssembly – metoda
Vrátí kontejner sestavení tohoto `ICorDebugAssembly3` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppAssembly`  
 Ukazatel na adresu ICorDebugAssembly objekt, který představuje kontejner sestavení nebo **null** Pokud selže volání metody.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` Pokud je úspěšné volání metody; v opačném `S_FALSE`, a `ppAssembly` je **null**.  
  
## <a name="remarks"></a>Poznámky  
 Pokud toto sestavení byl sloučen s ostatními uvnitř sestavení jediný kontejner, tato metoda vrátí kontejner sestavení. Další informace a přehled terminologie, najdete v článku [icordebugprocess6::enablevirtualmodulesplitting –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) tématu.  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugAssembly3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
