---
title: CorDebugInterfaceVersion – výčet
ms.date: 03/30/2017
api_name:
- CorDebugInterfaceVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInterfaceVersion
helpviewer_keywords:
- CorDebugInterfaceVersion enumeration [.NET Framework debugging]
ms.assetid: 7d1e6cd9-2a15-41c6-9b68-008705a4ed90
topic_type:
- apiref
ms.openlocfilehash: 5ebbbf01bc27974850c7e0bb3591b8f050fd0579
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179263"
---
# <a name="cordebuginterfaceversion-enumeration"></a>CorDebugInterfaceVersion – výčet
Určuje rozhraní, verzi rozhraní .NET Framework nebo verzi rozhraní .NET Framework, ve které bylo rozhraní zavedeno.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugInterfaceVersion {  
  
    CorDebugInvalidVersion            = 0,  
    CorDebugVersion_1_0               = CorDebugInvalidVersion + 1,  
  
    ver_ICorDebugManagedCallback      = CorDebugVersion_1_0,  
    ver_ICorDebugUnmanagedCallback    = CorDebugVersion_1_0,  
    ver_ICorDebug                     = CorDebugVersion_1_0,  
    ver_ICorDebugController           = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomain            = CorDebugVersion_1_0,  
    ver_ICorDebugAssembly             = CorDebugVersion_1_0,  
    ver_ICorDebugProcess              = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpoint           = CorDebugVersion_1_0,  
    ver_ICorDebugFunctionBreakpoint   = CorDebugVersion_1_0,  
    ver_ICorDebugModuleBreakpoint     = CorDebugVersion_1_0,  
    ver_ICorDebugValueBreakpoint      = CorDebugVersion_1_0,  
    ver_ICorDebugStepper              = CorDebugVersion_1_0,  
    ver_ICorDebugRegisterSet          = CorDebugVersion_1_0,  
    ver_ICorDebugThread               = CorDebugVersion_1_0,  
    ver_ICorDebugChain                = CorDebugVersion_1_0,  
    ver_ICorDebugFrame                = CorDebugVersion_1_0,  
    ver_ICorDebugILFrame              = CorDebugVersion_1_0,  
    ver_ICorDebugNativeFrame          = CorDebugVersion_1_0,  
    ver_ICorDebugModule               = CorDebugVersion_1_0,  
    ver_ICorDebugFunction             = CorDebugVersion_1_0,  
    ver_ICorDebugCode                 = CorDebugVersion_1_0,  
    ver_ICorDebugClass                = CorDebugVersion_1_0,  
    ver_ICorDebugEval                 = CorDebugVersion_1_0,  
    ver_ICorDebugValue                = CorDebugVersion_1_0,  
    ver_ICorDebugGenericValue         = CorDebugVersion_1_0,  
    ver_ICorDebugReferenceValue       = CorDebugVersion_1_0,  
    ver_ICorDebugHeapValue            = CorDebugVersion_1_0,  
    ver_ICorDebugObjectValue          = CorDebugVersion_1_0,  
    ver_ICorDebugBoxValue             = CorDebugVersion_1_0,  
    ver_ICorDebugStringValue          = CorDebugVersion_1_0,  
    ver_ICorDebugArrayValue           = CorDebugVersion_1_0,  
    ver_ICorDebugContext              = CorDebugVersion_1_0,  
    ver_ICorDebugEnum                 = CorDebugVersion_1_0,  
    ver_ICorDebugObjectEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpointEnum       = CorDebugVersion_1_0,  
    ver_ICorDebugStepperEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugProcessEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugThreadEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugFrameEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugChainEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugModuleEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugValueEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugCodeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugTypeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugErrorInfoEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomainEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAssemblyEnum         = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueErrorInfo
                                      = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueSnapshot
                                      = CorDebugVersion_1_0,  
  
    CorDebugVersion_1_1               = CorDebugVersion_1_0 + 1,  
    // No interface definitions in version 1.1.  
  
    CorDebugVersion_2_0 = CorDebugVersion_1_1 + 1,  
  
    ver_ICorDebugManagedCallback2    = CorDebugVersion_2_0,  
    ver_ICorDebugAppDomain2          = CorDebugVersion_2_0,  
    ver_ICorDebugProcess2            = CorDebugVersion_2_0,  
    ver_ICorDebugStepper2            = CorDebugVersion_2_0,  
    ver_ICorDebugRegisterSet2        = CorDebugVersion_2_0,  
    ver_ICorDebugThread2             = CorDebugVersion_2_0,  
    ver_ICorDebugILFrame2            = CorDebugVersion_2_0,  
    ver_ICorDebugModule2             = CorDebugVersion_2_0,  
    ver_ICorDebugFunction2           = CorDebugVersion_2_0,  
    ver_ICorDebugCode2               = CorDebugVersion_2_0,  
    ver_ICorDebugClass2              = CorDebugVersion_2_0,  
    ver_ICorDebugValue2              = CorDebugVersion_2_0,  
    ver_ICorDebugEval2               = CorDebugVersion_2_0,  
    ver_ICorDebugObjectValue2        = CorDebugVersion_2_0,  
  
    // CLR v4 - next major CLR version after CLR v2  
    // Includes Silverlight 4  
    CorDebugVersion_4_0 = CorDebugVersion_2_0 + 1,  
  
    ver_ICorDebugThread3             = CorDebugVersion_4_0,  
    ver_ICorDebugThread4             = CorDebugVersion_4_0,  
    ver_ICorDebugStackWalk           = CorDebugVersion_4_0,  
    ver_ICorDebugNativeFrame2        = CorDebugVersion_4_0,  
    ver_ICorDebugInternalFrame2      = CorDebugVersion_4_0,  
    ver_ICorDebugRuntimeUnwindableFrame = CorDebugVersion_4_0,  
    ver_ICorDebugHeapValue3          = CorDebugVersion_4_0,  
    ver_ICorDebugBlockingObjectEnum  = CorDebugVersion_4_0,  
    ver_ICorDebugValue3 = CorDebugVersion_4_0,  
  
    CorDebugVersion_4_5 = CorDebugVersion_4_0 + 1,  
  
    ver_ICorDebugComObjectValue = CorDebugVersion_4_5,  
    ver_ICorDebugAppDomain3 = CorDebugVersion_4_5,  
    ver_ICorDebugCode3 = CorDebugVersion_4_5,  
    ver_ICorDebugILFrame3 = CorDebugVersion_4_5,  
  
    CorDebugLatestVersion = CorDebugVersion_4_5  
  
} CorDebugInterfaceVersion;  
```  
  
## <a name="members"></a>Členové  
 Následující tabulka obsahuje odkazy z každé hodnoty výčtu na odpovídající rozhraní. Kromě toho tabulka označuje první verzi rozhraní .NET Framework, ve které bylo rozhraní podporováno.  
  
|Člen|Určuje|Verze rozhraní .NET Framework|  
|------------|---------------|----------------------------|  
|`CorDebugInvalidVersion`|Verze rozhraní .NET Framework je neplatná.|-|  
|`CorDebugVersion_1_0`|Verze rozhraní .NET Framework, včetně všech jeho aktualizací Service Pack, je 1.0.|1.0|  
|`CorDebugVersion_1_1`|Verze rozhraní .NET Framework, včetně všech aktualizací Service Pack, je 1.1.|1.1|  
|`CorDebugVersion_2_0`|Verze rozhraní .NET Framework, včetně všech aktualizací Service Pack, je 2.0.|2.0|  
|`CorDebugVersion_4_0`|Verze rozhraní .NET Framework, včetně všech aktualizací Service Pack, je 4.|4|  
|`CorDebugVersion_4_5`|Verze rozhraní .NET Framework, včetně všech aktualizací Service Pack, je 4.5.|4.5|  
|`ver_ICorDebugManagedCallback`|[ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)|1.0|  
|`ver_ICorDebugUnmanagedCallback`|[ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md)|1.0|  
|`ver_ICorDebug`|[ICorDebug](icordebug-interface.md)|1.0|  
|`ver_ICorDebugController`|[Řadič ICorDebugController](icordebugcontroller-interface.md)|1.0|  
|`ver_ICorDebugAppDomain`|[Doména ICorDebugAppDomain](icordebugappdomain-interface.md)|1.0|  
|`ver_ICorDebugAssembly`|[ICorDebugAssembly](icordebugassembly-interface.md)|1.0|  
|`ver_ICorDebugProcess`|[Proces iCordebugProcess](icordebugprocess-interface.md)|1.0|  
|`ver_ICorDebugBreakpoint`|[ICorDebugBreakpoint](icordebugbreakpoint-interface.md)|1.0|  
|`ver_ICorDebugFunctionBreakpoint`|[ICorDebugFunctionBreakpoint](icordebugfunctionbreakpoint-interface.md)|1.0|  
|`ver_ICorDebugModuleBreakpoint`|[ICorDebugModuleBreakpoint](icordebugmodulebreakpoint-interface.md)|1.0|  
|`ver_ICorDebugValueBreakpoint`|[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)|1.0|  
|`ver_ICorDebugStepper`|[ICorDebugStepper](icordebugstepper-interface.md)|1.0|  
|`ver_ICorDebugRegisterSet`|[ICorDebugRegisterSet](icordebugregisterset-interface.md)|1.0|  
|`ver_ICorDebugThread`|[ICorDebugThread](icordebugthread-interface.md)|1.0|  
|`ver_ICorDebugChain`|[ICorDebugChain](icordebugchain-interface.md)|1.0|  
|`ver_ICorDebugFrame`|[ICorDebugFrame](icordebugframe-interface.md)|1.0|  
|`ver_ICorDebugILFrame`|[ICorDebugILRám](icordebugilframe-interface.md)|1.0|  
|`ver_ICorDebugNativeFrame`|[ICorDebugNativeFrame](icordebugnativeframe-interface.md)|1.0|  
|`ver_ICorDebugModule`|[Modul ICorDebug](icordebugmodule-interface.md)|1.0|  
|`ver_ICorDebugFunction`|[ICorDebugFunction](icordebugfunction-interface1.md)|1.0|  
|`ver_ICorDebugCode`|[ICorDebugCode](icordebugcode-interface1.md)|1.0|  
|`ver_ICorDebugClass`|[Třída ICorDebugClass](icordebugclass-interface.md)|1.0|  
|`ver_ICorDebugEval`|[ICorDebugEval](icordebugeval-interface.md)|1.0|  
|`ver_ICorDebugValue`|[Hodnota ICorDebugValue](icordebugvalue-interface.md)|1.0|  
|`ver_ICorDebugGenericValue`|[ICorDebugGenericValue](icordebuggenericvalue-interface.md)|1.0|  
|`ver_ICorDebugReferenceValue`|[Hodnota ICorDebugReferenceValue](icordebugreferencevalue-interface.md)|1.0|  
|`ver_ICorDebugHeapValue`|[Hodnota heapdek iCorDebug](icordebugheapvalue-interface.md)|1.0|  
|`ver_ICorDebugObjectValue`|[Hodnota ICorDebugObjectValue](icordebugobjectvalue-interface.md)|1.0|  
|`ver_ICorDebugBoxValue`|[Hodnota iCorDebugBoxValue](icordebugboxvalue-interface.md)|1.0|  
|`ver_ICorDebugStringValue`|[Hodnota iCorDebugStringValue](icordebugstringvalue-interface.md)|1.0|  
|`ver_ICorDebugArrayValue`|[Hodnota ICorDebugArrayValue](icordebugarrayvalue-interface.md)|1.0|  
|`ver_ICorDebugContext`|[ICorDebugContext](icordebugcontext-interface.md)|1.0|  
|`ver_ICorDebugEnum`|[ICorDebugEnum](icordebugenum-interface1.md)|1.0|  
|`ver_ICorDebugObjectEnum`|[ICorDebugObjectEnum](icordebugobjectenum-interface.md)|1.0|  
|`ver_ICorDebugBreakpointEnum`|[ICorDebugBreakpointEnum](icordebugbreakpointenum-interface.md)|1.0|  
|`ver_ICorDebugStepperEnum`|[ICorDebugStepperEnum](icordebugstepperenum-interface.md)|1.0|  
|`ver_ICorDebugProcessEnum`|[ICorDebugProcessEnum](icordebugprocessenum-interface.md)|1.0|  
|`ver_ICorDebugThreadEnum`|[ICorDebugThreadEnum](icordebugthreadenum-interface1.md)|1.0|  
|`ver_ICorDebugFrameEnum`|[ICorDebugFrameEnum](icordebugframeenum-interface.md)|1.0|  
|`ver_ICorDebugChainEnum`|[ICorDebugChainEnum](icordebugchainenum-interface.md)|1.0|  
|`ver_ICorDebugModuleEnum`|[ICorDebugModuleEnum](icordebugmoduleenum-interface.md)|1.0|  
|`ver_ICorDebugValueEnum`|[ICorDebugValueEnum](icordebugvalueenum-interface.md)|1.0|  
|`ver_ICorDebugCodeEnum`|[ICorDebugCodeEnum](icordebugcodeenum-interface.md)|1.0|  
|`ver_ICorDebugTypeEnum`|[ICorDebugTypeEnum](icordebugtypeenum-interface.md)|1.0|  
|`ver_ICorDebugErrorInfoEnum`|[ICorDebugErrorInfoEnum](icordebugerrorinfoenum-interface.md)|1.0|  
|`ver_ICorDebugAppDomainEnum`|[ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md)|1.0|  
|`ver_ICorDebugAssemblyEnum`|[ICorDebugAssemblyEnum](icordebugassemblyenum-interface.md)|1.0|  
|`ver_ICorDebugEditAndContinueErrorInfo`|[ICorDebugEditAndContinueErrorInfo](icordebugeditandcontinueerrorinfo-interface.md)|1.0|  
|`ver_ICorDebugEditAndContinueSnapshot`|[ICorDebugEditAndContinueSnapshot](icordebugeditandcontinuesnapshot-interface.md)|1.0|  
|`ver_ICorDebugManagedCallback2`|[ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)|2.0|  
|`ver_ICorDebugAppDomain2`|[ICorDebugAppDomain2](icordebugappdomain2-interface.md)|2.0|  
|`ver_ICorDebugProcess2`|[ICorDebugProcess2](icordebugprocess2-interface1.md)|2.0|  
|`ver_ICorDebugStepper2`|[ICorDebugStepper2](icordebugstepper2-interface1.md)|2.0|  
|`ver_ICorDebugRegisterSet2`|[ICorDebugRegisterSet2](icordebugregisterset2-interface.md)|2.0|  
|`ver_ICorDebugThread2`|[ICorDebugThread2](icordebugthread2-interface.md)|2.0|  
|`ver_ICorDebugILFrame2`|[ICorDebugIL2](icordebugilframe2-interface.md)|2.0|  
|`ver_ICorDebugModule2`|[ICorDebugModule2](icordebugmodule2-interface.md)|2.0|  
|`ver_ICorDebugFunction2`|[Funkce ICorDebug2](icordebugfunction2-interface.md)|2.0|  
|`ver_ICorDebugCode2`|[ICorDebugCode2](icordebugcode2-interface.md)|2.0|  
|`ver_ICorDebugClass2`|"ICorDebugClass2"|2.0|  
|`ver_ICorDebugValue2`|"ICorDebugValue2"|2.0|  
|`ver_ICorDebugEval2`|"ICorDebugEval2".|2.0|  
|`ver_ICorDebugObjectValue2`|"ICorDebugObjectValue2"|2.0|  
|`ver_ICorDebugThread3`|[ICorDebugThread3](icordebugthread3-interface.md)|4|  
|`ver_ICorDebugThread4`|[ICorDebugThread4](icordebugthread4-interface.md)|4|  
|`ver_ICorDebugStackWalk`|[ICorDebugStackWalk](icordebugstackwalk-interface.md)|4|  
|`ver_ICorDebugNativeFrame2`|[ICorDebugNativeFrame2](icordebugnativeframe2-interface.md)|4|  
|`ver_ICorDebugInternalFrame2`|[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)|4|  
|`ver_ICorDebugRuntimeUnwindableFrame`|[ICorDebugRuntimeUnwindableFrame](icordebugruntimeunwindableframe-interface.md)|4|  
|`ver_ICorDebugHeapValue3`|[ICorDebugHeapValue3 – rozhraní](icordebugheapvalue3-interface.md)|4|  
|`ver_ICorDebugBlockingObjectEnum`|[ICorDebugBlockingObjectEnum – rozhraní](icordebugblockingobjectenum-interface.md)|4|  
|`ver_ICorDebugValue3`|[Hodnota ICorDebugValue3](icordebugvalue3-interface.md)|4|  
|`ver_ICorDebugComObjectValue`|[Hodnota ICorDebugComObjectValue](icordebugcomobjectvalue-interface.md)|4.5|  
|`ver_ICorDebugAppDomain3`|[ICorDebugAppDomain3](icordebugappdomain3-interface.md)|4.5|  
|`ver_ICorDebugCode3`|[ICorDebugCode3](icordebugcode3-interface.md)|4.5|  
|`ver_ICorDebugILFrame3`|[ICorDebugILFrame3](icordebugilframe3-interface.md)|4.5|  
|`CorDebugLatestVersion`|Nejnovější verzí je verze rozhraní .NET Framework, včetně všech jejích aktualizací Service Pack.|-|  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program můžete `CorDebugInterfaceVersion` použít výčet v [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) funkce určit nejvyšší verzi rozhraní .NET Framework, který podporuje ladicí program.  
  
## <a name="interface-names"></a>Názvy rozhraní  
 Číslo, které se zobrazí na konci názvů rozhraní v rozhraní API pro ladění `ICorDebugThread3`(například "3" v ) určuje verzi rozhraní, nikoli verzi rozhraní .NET Framework. Všechny názvy rozhraní v rozhraní API ladění zahrnují čísla verzí s výjimkou rozhraní, která byla zavedena v rozhraní .NET Framework verze 1. Jakákoli korespondence mezi čísly verzí rozhraní and.NET čísla verzí rozhraní jsou náhodná.  
  
- Rozhraní, která byla zavedena v rozhraní .NET Framework verze 1.0 neobsahují čísla, protože jsou všechny implicitně verze 1.  
  
- Rozhraní .NET Framework verze 1.1 používá rozhraní verze 1.0 a nezavádí žádná nová ladicí rozhraní.  
  
- 14 ladicí rozhraní zavedená v rozhraní .NET Framework verze 2.0 jsou logická rozšíření jejich protějšky verze 1 a zahrnují číslo "2" v jejich názvech.  
  
- Rozhraní .NET Framework verze 3.0 a 3.5 používají existující rozhraní rozhraní rozhraní .NET Framework 2.0 a nezavádějí žádná nová rozhraní.  
  
- Rozhraní .NET Framework 4 zavádí kombinaci verzí rozhraní. Například oba `ICorDebugThread3` `ICorDebugThread4` a zobrazí se jako třetí `ICorDebugThread` a čtvrtá verze rozhraní. Rozhraní .NET Framework 4 také zavádí `ICorDebugStackWalk` první verzi rozhraní a `ICorDebugNativeFrame` druhou`ICorDebugNativeFrame2`verzi rozhraní ( ).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro ladění](debugging-enumerations.md)
