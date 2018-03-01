---
title: "CorDebugRegister – výčet"
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
- CorDebugRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugRegister
helpviewer_keywords:
- CorDebugRegister enumeration [.NET Framework debugging]
ms.assetid: 003bb138-7960-4291-ac88-0d87e470ff70
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3f168e686a127b2763099d2cfaea7ff396c4e734
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugregister-enumeration"></a>CorDebugRegister – výčet
Určuje registry spojené s danou procesoru architektura.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugRegister {  
  
    REGISTER_INSTRUCTION_POINTER = 0,  
    REGISTER_STACK_POINTER,  
    REGISTER_FRAME_POINTER,  
  
    REGISTER_X86_EIP = 0,  
    REGISTER_X86_ESP,  
    REGISTER_X86_EBP,  
  
    REGISTER_X86_EAX,  
    REGISTER_X86_ECX,  
    REGISTER_X86_EDX,  
    REGISTER_X86_EBX,  
  
    REGISTER_X86_ESI,  
    REGISTER_X86_EDI,  
  
    REGISTER_X86_FPSTACK_0,  
    REGISTER_X86_FPSTACK_1,  
    REGISTER_X86_FPSTACK_2,  
    REGISTER_X86_FPSTACK_3,  
    REGISTER_X86_FPSTACK_4,  
    REGISTER_X86_FPSTACK_5,  
    REGISTER_X86_FPSTACK_6,  
    REGISTER_X86_FPSTACK_7,  
  
    REGISTER_AMD64_RIP = 0,  
    REGISTER_AMD64_RSP,  
    REGISTER_AMD64_RBP,  
    REGISTER_AMD64_RAX,  
    REGISTER_AMD64_RCX,  
    REGISTER_AMD64_RDX,  
    REGISTER_AMD64_RBX,  
    REGISTER_AMD64_RSI,  
    REGISTER_AMD64_RDI,  
    REGISTER_AMD64_R8,  
    REGISTER_AMD64_R9,  
    REGISTER_AMD64_R10,  
    REGISTER_AMD64_R11,  
    REGISTER_AMD64_R12,  
    REGISTER_AMD64_R13,  
    REGISTER_AMD64_R14,  
    REGISTER_AMD64_R15,  
  
    REGISTER_AMD64_XMM0,  
    REGISTER_AMD64_XMM1,  
    REGISTER_AMD64_XMM2,  
    REGISTER_AMD64_XMM3,  
    REGISTER_AMD64_XMM4,  
    REGISTER_AMD64_XMM5,  
    REGISTER_AMD64_XMM6,  
    REGISTER_AMD64_XMM7,  
    REGISTER_AMD64_XMM8,  
    REGISTER_AMD64_XMM9,  
    REGISTER_AMD64_XMM10,  
    REGISTER_AMD64_XMM11,  
    REGISTER_AMD64_XMM12,  
    REGISTER_AMD64_XMM13,  
    REGISTER_AMD64_XMM14,  
    REGISTER_AMD64_XMM15,  
  
    REGISTER_IA64_BSP = REGISTER_FRAME_POINTER,  
    REGISTER_IA64_R0  = REGISTER_IA64_BSP + 1,  
    REGISTER_IA64_F0  = REGISTER_IA64_R0  + 128,  
    REGISTER_ARM_PC = 0,  
    REGISTER_ARM_SP,  
    REGISTER_ARM_R0,  
    REGISTER_ARM_R1,  
    REGISTER_ARM_R2,  
    REGISTER_ARM_R3,  
    REGISTER_ARM_R4,  
    REGISTER_ARM_R5,  
    REGISTER_ARM_R6,  
    REGISTER_ARM_R7,  
    REGISTER_ARM_R8,  
    REGISTER_ARM_R9,  
    REGISTER_ARM_R10,  
    REGISTER_ARM_R11,  
    REGISTER_ARM_R12,  
    REGISTER_ARM_LR,  
  
} CorDebugRegister;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`REGISTER_INSTRUCTION_POINTER`|Ukazatele instrukce zaregistrovat na jakýkoli procesor.|  
|`REGISTER_STACK_POINTER`|Ukazatel zásobníku zaregistrovat na jakýkoli procesor.|  
|`REGISTER_FRAME_POINTER`|Ukazatel na rámec zaregistrovat na jakýkoli procesor.|  
|`REGISTER_X86_EIP`|Registrace ukazatel instrukce na x86 procesoru.|  
|`REGISTER_X86_ESP`|Registrace ukazatel zásobníku na x86 procesoru.|  
|`REGISTER_X86_EBP`|Registr základní ukazatele na x86 procesoru.|  
|`REGISTER_X86_EAX`|A data zaregistrujte na x86 procesoru.|  
|`REGISTER_X86_ECX`|C data zaregistrovat na x86 procesoru.|  
|`REGISTER_X86_EDX`|D data zaregistrovat na x86 procesoru.|  
|`REGISTER_X86_EBX`|B data zaregistrovat na x86 procesoru.|  
|`REGISTER_X86_ESI`|Index registrace zdroje na x86 procesoru.|  
|`REGISTER_X86_EDI`|Registrace index cílového na x86 procesoru.|  
|`REGISTER_X86_FPSTACK_0`|Procesor registrace 0 na s plovoucí desetinnou čárkou x86 (FP) zásobníku.|  
|`REGISTER_X86_FPSTACK_1`|Zásobník #1 zaregistrovat na x86 FP procesoru.|  
|`REGISTER_X86_FPSTACK_2`|Zásobník #2 zaregistrovat na x86 FP procesoru.|  
|`REGISTER_X86_FPSTACK_3`|Zásobník #3 zaregistrovat na x86 FP procesoru.|  
|`REGISTER_X86_FPSTACK_4`|Zásobník #4 zaregistrovat na x86 FP procesoru.|  
|`REGISTER_X86_FPSTACK_5`|Zásobník #5 zaregistrovat na x86 FP procesoru.|  
|`REGISTER_X86_FPSTACK_6`|Zásobník #6 zaregistrovat na x86 FP procesoru.|  
|`REGISTER_X86_FPSTACK_7`|Zásobník #7 zaregistrovat na x86 FP procesoru.|  
|`REGISTER_AMD64_RIP`|Ukazatel instrukce zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_RSP`|Ukazatel zásobníku zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_RBP`|Základní ukazatele zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_RAX`|A data zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_RCX`|C data zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_RDX`|D data zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_RBX`|B data zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_RSI`|Index zdroje zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_RDI`|Cílový index zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_R8`|Data #8 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_R9`|Data #9 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_R10`|Data #10 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_R11`|Data #11 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_R12`|Data #12 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_R13`|Data #13 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_R14`|Data #14 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_R15`|Data #15 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_XMM0`|Multimediální #0 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_XMM1`|Multimediální #1 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_XMM2`|Multimediální #2 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_XMM3`|Multimediální #3 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_XMM4`|Multimediální #4 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_XMM5`|Multimediální #5 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_XMM6`|Multimediální #6 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_XMM7`|Multimediální #7 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_XMM8`|Multimediální #8 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_XMM9`|Multimediální #9 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_XMM10`|Multimediální #10 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_XMM11`|Multimediální #11 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_XMM12`|Multimediální #12 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_XMM13`|Multimediální #13 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_XMM14`|Multimediální #14 zaregistrovat na procesoru AMD64.|  
|`REGISTER_AMD64_XMM15`|Multimediální #15 zaregistrovat na procesoru AMD64.|  
|`REGISTER_IA64_BSP`|Ukazatel zásobníku zaregistrovat na procesoru IA-64.|  
|`REGISTER_IA64_R0`|Data #0 zaregistrovat na procesoru IA-64.|  
|`REGISTER_IA64_F0`|Data FP #0 zaregistrovat na procesoru IA-64.|  
|`REGISTER_ARM_PC`|Čítač programu zaregistrovat na procesor ARM (R15).|  
|`REGISTER_ARM_SP`|Ukazatel zásobníku zaregistrovat na procesor ARM (R13).|  
|`REGISTER_ARM_R0`|Data zaregistrovat R0 na procesor ARM.|  
|`REGISTER_ARM_R1`|Data zaregistrovat R1 na procesor ARM.|  
|`REGISTER_ARM_R2`|Data zaregistrovat R2 na procesor ARM.|  
|`REGISTER_ARM_R3`|Data zaregistrovat R3 na procesor ARM.|  
|`REGISTER_ARM_R4`|Zaregistrujte R4 na procesor ARM.|  
|`REGISTER_ARM_R5`|Zaregistrujte R5 na procesor ARM.|  
|`REGISTER_ARM_R6`|Zaregistrujte R6 na procesor ARM.|  
|`REGISTER_ARM_R7`|Zaregistrovat R7 (Flash ukazatel na rámec) v procesoru ARM.|  
|`REGISTER_ARM_R8`|Zaregistrujte R8 na procesor ARM.|  
|`REGISTER_ARM_R9`|Zaregistrujte R9 na procesor ARM.|  
|`REGISTER_ARM_R10`|Zaregistrujte R10 na procesor ARM.|  
|`REGISTER_ARM_R11`|Ukazatele na rámec u procesoru ARM.|  
|`REGISTER_ARM_R12`|Zaregistrujte r 12 na procesor ARM.|  
|`REGISTER_ARM_LR`|Odkaz zaregistrovat na procesor ARM (R14).|  
  
## <a name="remarks"></a>Poznámky  
 Existují 128 pro obecné účely datových registrů a 128 s plovoucí desetinnou čárkou datových registrů na procesoru IA-64, ale pouze hodnoty `REGISTER_IA64_R0` a `REGISTER_IA64_F0` jsou k dispozici. Ostatní hodnoty lze se určí takto:  
  
-   Přidat číslo registrace pro `REGISTER_IA64_R0` pro hodnoty `REGISTER_IA64_R1` prostřednictvím `REGISTER_IA64_R127`, které odpovídají registr #1 dat prostřednictvím registrace #127 data na procesoru IA-64.  
  
-   Přidat číslo registrace pro `REGISTER_IA64_F0` pro hodnoty `REGISTER_IA64_F1` prostřednictvím `REGISTER_IA64_F127`, které odpovídají registr dat FP #1 až #127 FP registr dat na procesoru IA-64.  
  
 Například pokud je třeba zadat registr #83 dat na procesoru IA-64, použijte `REGISTER_IA64_R0` + 83.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
