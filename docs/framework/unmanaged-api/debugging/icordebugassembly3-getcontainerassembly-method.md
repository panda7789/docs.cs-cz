---
title: ICorDebugAssembly3::GetContainerAssembly – metoda
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9bd4cd44eca9b12ab8773fd75b6262579cfe8e8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206080"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a>ICorDebugAssembly3::GetContainerAssembly – metoda
Vrátí kontejner sestavení tohoto `ICorDebugAssembly3` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppAssembly`  
 Ukazatel na adresu icordebugassembly – objekt, který představuje kontejner sestavení nebo **null** Pokud selže volání metody.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` Pokud volání metody, které úspěšně. v opačném případě `S_FALSE`, a `ppAssembly` je **null**.  
  
## <a name="remarks"></a>Poznámky  
 Pokud toto sestavení bylo sloučeno s jinými uživateli uvnitř sestavení jednoho kontejneru, tato metoda vrátí sestavení kontejneru. Další informace a terminologii, najdete v článku [icordebugprocess6::enablevirtualmodulesplitting –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) tématu.  
  
> [!NOTE]
>  Tato metoda je pouze k dispozici s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní ICorDebugAssembly3](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [Debugging – rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
