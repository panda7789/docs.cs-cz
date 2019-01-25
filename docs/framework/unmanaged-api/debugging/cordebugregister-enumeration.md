---
title: CorDebugRegister – výčet
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4175cf26b783ab7f19905941e94cfdb15ce69cff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694058"
---
# <a name="cordebugregister-enumeration"></a>CorDebugRegister – výčet
Určuje registrů spojené s danou procesor architektury.  
  
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
|`REGISTER_INSTRUCTION_POINTER`|Ukazatele na instrukci zaregistrovat na jakýkoli procesor.|  
|`REGISTER_STACK_POINTER`|Ukazatel zásobníku zaregistrovat na jakýkoli procesor.|  
|`REGISTER_FRAME_POINTER`|Ukazatel na rámec zaregistrovat na jakýkoli procesor.|  
|`REGISTER_X86_EIP`|Instrukce registr ukazatelů na x86 procesoru.|  
|`REGISTER_X86_ESP`|Zásobník registr ukazatelů na x86 procesoru.|  
|`REGISTER_X86_EBP`|Registr základního ukazatele na x86 procesoru.|  
|`REGISTER_X86_EAX`|A data zaregistrujte na x86 procesoru.|  
|`REGISTER_X86_ECX`|Registr dat C na x86 procesoru.|  
|`REGISTER_X86_EDX`|D data registrovat x86 procesoru.|  
|`REGISTER_X86_EBX`|Registr B dat na x86 procesoru.|  
|`REGISTER_X86_ESI`|Registr indexu zdroje na x86 procesoru.|  
|`REGISTER_X86_EDI`|Určení registr indexu na x86 procesoru.|  
|`REGISTER_X86_FPSTACK_0`|Procesor registru 0 na s plovoucí desetinnou čárkou x86 (FP) zásobníku.|  
|`REGISTER_X86_FPSTACK_1`|#1 zásobníku zaregistrovat na x86 FP procesoru.|  
|`REGISTER_X86_FPSTACK_2`|#2 zásobníku zaregistrovat na x86 FP procesoru.|  
|`REGISTER_X86_FPSTACK_3`|#3 zásobníku zaregistrovat na x86 FP procesoru.|  
|`REGISTER_X86_FPSTACK_4`|#4 zásobníku zaregistrovat na x86 FP procesoru.|  
|`REGISTER_X86_FPSTACK_5`|#5 zásobníku zaregistrovat na x86 FP procesoru.|  
|`REGISTER_X86_FPSTACK_6`|#6 zásobníku zaregistrovat na x86 FP procesoru.|  
|`REGISTER_X86_FPSTACK_7`|#7 zásobníku zaregistrovat na x86 FP procesoru.|  
|`REGISTER_AMD64_RIP`|Ukazatele na instrukci zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_RSP`|Ukazatel zásobníku zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_RBP`|Registr základního ukazatele na procesor AMD64.|  
|`REGISTER_AMD64_RAX`|A data zaregistrujte na procesor AMD64.|  
|`REGISTER_AMD64_RCX`|C data zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_RDX`|D data zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_RBX`|B data zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_RSI`|Index zdroje zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_RDI`|Cílový index zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_R8`|Data #8 zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_R9`|Data #9 zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_R10`|Data #10 zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_R11`|Data #11 zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_R12`|Data #12 zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_R13`|Data #13 zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_R14`|Data #14 zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_R15`|Data #15 zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_XMM0`|Multimediální #0 zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_XMM1`|Multimediální #1 zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_XMM2`|Multimediální #2 zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_XMM3`|Multimediální #3 zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_XMM4`|Multimediální #4 zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_XMM5`|Multimediální #5 zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_XMM6`|Multimediální #6 zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_XMM7`|Multimediální #7 zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_XMM8`|Multimediální #8 zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_XMM9`|Multimediální #9 zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_XMM10`|Multimediální #10 se zaregistrujte na procesor AMD64.|  
|`REGISTER_AMD64_XMM11`|Multimediální #11 zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_XMM12`|Multimediální #12 se zaregistrujte na procesor AMD64.|  
|`REGISTER_AMD64_XMM13`|Multimediální #13 zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_XMM14`|Multimediální #14 zaregistrovat na procesor AMD64.|  
|`REGISTER_AMD64_XMM15`|Multimediální #15 zaregistrovat na procesor AMD64.|  
|`REGISTER_IA64_BSP`|Ukazatel zásobníku zaregistrovat na procesor IA-64.|  
|`REGISTER_IA64_R0`|Data #0 zaregistrovat na procesor IA-64.|  
|`REGISTER_IA64_F0`|Data FP #0 zaregistrovat na procesor IA-64.|  
|`REGISTER_ARM_PC`|Čítač programu registrace (R15) na procesoru ARM.|  
|`REGISTER_ARM_SP`|Ukazatel zásobníku zaregistrovat na procesoru ARM (R13).|  
|`REGISTER_ARM_R0`|Data zaregistrovat R0 na procesoru ARM.|  
|`REGISTER_ARM_R1`|R1 registr dat na procesoru ARM.|  
|`REGISTER_ARM_R2`|Data zaregistrovat R2 na procesoru ARM.|  
|`REGISTER_ARM_R3`|Data zaregistrovat R3 na procesoru ARM.|  
|`REGISTER_ARM_R4`|Zaregistrujte R4 na procesoru ARM.|  
|`REGISTER_ARM_R5`|Zaregistrujte R5 na procesoru ARM.|  
|`REGISTER_ARM_R6`|Zaregistrujte R6 na procesoru ARM.|  
|`REGISTER_ARM_R7`|Zaregistrujte R7 (THUMB ukazatel na rámec) na procesoru ARM.|  
|`REGISTER_ARM_R8`|Zaregistrujte R8 na procesoru ARM.|  
|`REGISTER_ARM_R9`|Zaregistrujte R9 na procesoru ARM.|  
|`REGISTER_ARM_R10`|Zaregistrujte R10 na procesoru ARM.|  
|`REGISTER_ARM_R11`|Ukazatele na rámce u procesoru ARM.|  
|`REGISTER_ARM_R12`|Zaregistrujte r 12 na procesoru ARM.|  
|`REGISTER_ARM_LR`|Odkaz na registraci (R14) na procesoru ARM.|  
  
## <a name="remarks"></a>Poznámky  
 Existují 128 pro obecné účely datových registrů a 128 s plovoucí desetinnou čárkou datových registrů na IA-64 procesorů, ale pouze hodnoty `REGISTER_IA64_R0` a `REGISTER_IA64_F0` jsou k dispozici. Ostatní hodnoty můžou být stanoven následujícím způsobem:  
  
-   Přidat registr číslo, které má `REGISTER_IA64_R0` pro hodnoty `REGISTER_IA64_R1` prostřednictvím `REGISTER_IA64_R127`, které odpovídají registr #1 dat prostřednictvím #127 data registru na procesor IA-64.  
  
-   Přidat registr číslo, které má `REGISTER_IA64_F0` pro hodnoty `REGISTER_IA64_F1` prostřednictvím `REGISTER_IA64_F127`, které odpovídají data registr FP #1 až #127 registr FP dat na procesor IA-64.  
  
 Například pokud je třeba zadat registr #83 dat na procesor IA-64, použijte `REGISTER_IA64_R0` + 83.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
