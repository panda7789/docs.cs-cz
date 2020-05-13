---
title: ICorDebugILFrame – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
ms.openlocfilehash: 1f1e42cd929d2d6282d282cf62dce00104b3a925
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210238"
---
# <a name="icordebugilframe-interface"></a>ICorDebugILFrame – rozhraní

Představuje rámec zásobníku kódu jazyka MSIL (Microsoft Intermediate Language). Toto rozhraní je podtřídou rozhraní ICorDebugFrame.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CanSetIP – metoda](icordebugilframe-cansetip-method.md)|Získá hodnotu, která označuje, zda je bezpečné nastavit ukazatel na instrukci na určené místo posunutí.|  
|[EnumerateArguments – metoda](icordebugilframe-enumeratearguments-method.md)|Získá enumerátor pro argumenty v tomto snímku.|  
|[EnumerateLocalVariables – metoda](icordebugilframe-enumeratelocalvariables-method.md)|Získá enumerátor pro místní proměnné v tomto snímku.|  
|[GetArgument – metoda](icordebugilframe-getargument-method.md)|Získá hodnotu zadaného argumentu v rámci tohoto bloku zásobníku MSIL.|  
|[GetIP – metoda](icordebugilframe-getip-method.md)|Získá hodnotu ukazatele na instrukci a bitovou kombinaci hodnoty, která popisuje, jak byla získána hodnota ukazatele na instrukci.|  
|[GetLocalVariable – metoda](icordebugilframe-getlocalvariable-method.md)|Získá hodnotu zadané místní proměnné v tomto bloku zásobníku MSIL.|  
|[GetStackDepth – metoda](icordebugilframe-getstackdepth-method.md)|Není implementováno.|  
|[GetStackValue – metoda](icordebugilframe-getstackvalue-method.md)|Není implementováno.|  
|[SetIP – metoda](icordebugilframe-setip-method.md)|Nastaví ukazatel na instrukci na zadané místo posunutí v kódu jazyka MSIL.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugILFrame`Rozhraní je specializované rozhraní ICorDebugFrame. Používá se buď pro rámečky kódu MSIL, nebo pro zkompilované snímky JIT (just-in-time). Rámce zkompilované JIT implementují `ICorDebugILFrame` rozhraní i rozhraní ICorDebugNativeFrame.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
