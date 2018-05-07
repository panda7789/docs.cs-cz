---
title: Výčet CorDebugCodeInvokeKind
ms.date: 03/30/2017
api_name:
- CorDebugCodeInvokeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: e795e6a2-1008-4a81-af88-d777888e942e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf777214c015f0bbc434e3123d3ec7ef7f723549
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugcodeinvokekind-enumeration"></a>Výčet CorDebugCodeInvokeKind
Popisuje, jak exportované funkce vyvolá spravovaného kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,       
    CODE_INVOKE_KIND_RETURN,     
    CODE_INVOKE_KIND_TAILCALL,   
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|Pokud je spravovaný kód je vyvolána touto metodou, bude mít umístěné explicitní události nebo zarážky později.<br /><br /> --nebo--<br /><br /> Právě jsme může neproběhly některé spravovaného kódu, který tato metoda volá, protože neexistuje žádný snadný způsob, jak zastavit v něm.<br /><br /> --nebo--<br /><br /> Metoda může vyvolat nikdy spravovaného kódu.|  
|`CODE_INVOKE_KIND_RETURN`|Tato metoda vyvolá spravovaného kódu pomocí návratový instrukcí. Krokování s by měl přicházejí na další spravovaného kódu.|  
|`CODE_INVOKE_KIND_TAILCALL`|Tato metoda vyvolá spravovaného kódu pomocí volání funkce tail. Krokování s jedním a zanoříte se některé pokyny volání měli přicházejí na spravovaný kód.|  
  
## <a name="remarks"></a>Poznámky  
 Tento výčet je používán [icordebugprocess6::getexportstepinfo –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) metoda s informacemi o procházení spravovaného kódu.  
  
> [!NOTE]
>  Tento výčet je určena pro použití v rozhraní .NET nativní ladění pouze scénáře.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
