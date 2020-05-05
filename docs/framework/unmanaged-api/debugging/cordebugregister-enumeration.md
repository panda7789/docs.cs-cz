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
ms.openlocfilehash: 19d0dcf8a5633371765861fcc29df4ef8c91ebc4
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795713"
---
# <a name="cordebugregister-enumeration"></a>CorDebugRegister – výčet
Určuje Registry přidružené k dané architektuře procesoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
|`REGISTER_INSTRUCTION_POINTER`|Registr ukazatele na instrukce pro libovolný procesor.|  
|`REGISTER_STACK_POINTER`|Registr ukazatele zásobníku na jakémkoli procesoru.|  
|`REGISTER_FRAME_POINTER`|Registr ukazatele na rámec u libovolného procesoru.|  
|`REGISTER_X86_EIP`|Registr ukazatele na instrukce pro procesor x86.|  
|`REGISTER_X86_ESP`|Registr ukazatele zásobníku v procesoru x86.|  
|`REGISTER_X86_EBP`|Základní ukazatel se registruje v procesoru x86.|  
|`REGISTER_X86_EAX`|Záznam dat v procesoru x86.|  
|`REGISTER_X86_ECX`|Registr dat C v procesoru x86.|  
|`REGISTER_X86_EDX`|Registr dat D v procesoru x86.|  
|`REGISTER_X86_EBX`|Registr dat B v procesoru x86.|  
|`REGISTER_X86_ESI`|Registr zdrojového indexu v procesoru x86.|  
|`REGISTER_X86_EDI`|Registr cílového indexu v procesoru x86.|  
|`REGISTER_X86_FPSTACK_0`|Registr zásobníku 0 v procesoru s plovoucí desetinnou čárkou (FP) x86.|  
|`REGISTER_X86_FPSTACK_1`|#1 registr zásobníku na procesoru x86 FP.|  
|`REGISTER_X86_FPSTACK_2`|#2 registr zásobníku na procesoru x86 FP.|  
|`REGISTER_X86_FPSTACK_3`|#3 registr zásobníku na procesoru x86 FP.|  
|`REGISTER_X86_FPSTACK_4`|#4 registr zásobníku na procesoru x86 FP.|  
|`REGISTER_X86_FPSTACK_5`|#5 registr zásobníku na procesoru x86 FP.|  
|`REGISTER_X86_FPSTACK_6`|#6 registr zásobníku na procesoru x86 FP.|  
|`REGISTER_X86_FPSTACK_7`|#7 registr zásobníku na procesoru x86 FP.|  
|`REGISTER_AMD64_RIP`|Registr ukazatele na instrukce pro procesor AMD64.|  
|`REGISTER_AMD64_RSP`|Registr ukazatele zásobníku v procesoru AMD64.|  
|`REGISTER_AMD64_RBP`|Základní ukazatel se registruje na procesoru AMD64.|  
|`REGISTER_AMD64_RAX`|Záznam dat na procesoru AMD64.|  
|`REGISTER_AMD64_RCX`|Registr dat C v procesoru AMD64.|  
|`REGISTER_AMD64_RDX`|Registr dat D v procesoru AMD64.|  
|`REGISTER_AMD64_RBX`|Registr dat B v procesoru AMD64.|  
|`REGISTER_AMD64_RSI`|Registr zdrojového indexu v procesoru AMD64.|  
|`REGISTER_AMD64_RDI`|Registr cílového indexu v procesoru AMD64.|  
|`REGISTER_AMD64_R8`|#8 registraci dat v procesoru AMD64.|  
|`REGISTER_AMD64_R9`|#9 registraci dat v procesoru AMD64.|  
|`REGISTER_AMD64_R10`|#10 registraci dat v procesoru AMD64.|  
|`REGISTER_AMD64_R11`|#11 registraci dat v procesoru AMD64.|  
|`REGISTER_AMD64_R12`|#12 registraci dat v procesoru AMD64.|  
|`REGISTER_AMD64_R13`|#13 registraci dat v procesoru AMD64.|  
|`REGISTER_AMD64_R14`|#14 registraci dat v procesoru AMD64.|  
|`REGISTER_AMD64_R15`|#15 registraci dat v procesoru AMD64.|  
|`REGISTER_AMD64_XMM0`|Registr #0 multimédií na procesorech AMD64.|  
|`REGISTER_AMD64_XMM1`|Registr #1 multimédií na procesorech AMD64.|  
|`REGISTER_AMD64_XMM2`|Registr #2 multimédií na procesorech AMD64.|  
|`REGISTER_AMD64_XMM3`|Registr #3 multimédií na procesorech AMD64.|  
|`REGISTER_AMD64_XMM4`|Registr #4 multimédií na procesorech AMD64.|  
|`REGISTER_AMD64_XMM5`|Registr #5 multimédií na procesorech AMD64.|  
|`REGISTER_AMD64_XMM6`|Registr #6 multimédií na procesorech AMD64.|  
|`REGISTER_AMD64_XMM7`|Registr #7 multimédií na procesorech AMD64.|  
|`REGISTER_AMD64_XMM8`|Registr #8 multimédií na procesorech AMD64.|  
|`REGISTER_AMD64_XMM9`|Registr #9 multimédií na procesorech AMD64.|  
|`REGISTER_AMD64_XMM10`|Registr #10 multimédií na procesorech AMD64.|  
|`REGISTER_AMD64_XMM11`|Registr #11 multimédií na procesorech AMD64.|  
|`REGISTER_AMD64_XMM12`|Registr #12 multimédií na procesorech AMD64.|  
|`REGISTER_AMD64_XMM13`|Registr #13 multimédií na procesorech AMD64.|  
|`REGISTER_AMD64_XMM14`|Registr #14 multimédií na procesorech AMD64.|  
|`REGISTER_AMD64_XMM15`|Registr #15 multimédií na procesorech AMD64.|  
|`REGISTER_IA64_BSP`|Registr ukazatele zásobníku v procesoru IA-64.|  
|`REGISTER_IA64_R0`|#0 registraci dat v procesoru IA-64.|  
|`REGISTER_IA64_F0`|Registr dat #0 FP v procesoru IA-64.|  
|`REGISTER_ARM_PC`|Registr čítače programu (R15) na procesoru ARM.|  
|`REGISTER_ARM_SP`|Registr ukazatele zásobníku (R13) na procesoru ARM.|  
|`REGISTER_ARM_R0`|R0 registru dat na procesor ARM.|  
|`REGISTER_ARM_R1`|Registrace dat R1 v procesoru ARM.|  
|`REGISTER_ARM_R2`|Data Registry R2 na procesoru ARM.|  
|`REGISTER_ARM_R3`|Data Register R3 na procesoru ARM.|  
|`REGISTER_ARM_R4`|Registrace R4 na procesoru ARM.|  
|`REGISTER_ARM_R5`|Zaregistrujte R5 na procesor ARM.|  
|`REGISTER_ARM_R6`|Zaregistrujte R6 na procesor ARM.|  
|`REGISTER_ARM_R7`|Zaregistrujte R7 (ukazatel na rámec jezdce) na procesoru ARM.|  
|`REGISTER_ARM_R8`|Zaregistrujte R8 na procesoru ARM.|  
|`REGISTER_ARM_R9`|Zaregistrujte R9 na procesor ARM.|  
|`REGISTER_ARM_R10`|Zaregistrujte R10 na procesor ARM.|  
|`REGISTER_ARM_R11`|Ukazatel na rámec na procesoru ARM.|  
|`REGISTER_ARM_R12`|Zaregistrujte R12 na procesor ARM.|  
|`REGISTER_ARM_LR`|Registr odkazů (R14) na procesoru ARM.|  
  
## <a name="remarks"></a>Poznámky  
 Pro procesor IA-64 jsou k dispozici 128 datových registrů pro obecné účely a 128 datových registrů s plovoucí desetinnou `REGISTER_IA64_R0` čárkou, ale jsou k dispozici pouze hodnoty a `REGISTER_IA64_F0` . Ostatní hodnoty lze určit následujícím způsobem:  
  
- Přidejte číslo registru do `REGISTER_IA64_R0` pro hodnoty `REGISTER_IA64_R1` prostřednictvím `REGISTER_IA64_R127`, který odpovídá #1 registraci dat prostřednictvím #127 registru pro procesor IA-64.  
  
- Přidejte číslo registru do `REGISTER_IA64_F0` pro hodnoty `REGISTER_IA64_F1` prostřednictvím `REGISTER_IA64_F127`, který odpovídá registru dat #1 FP prostřednictvím #127 registru dat FP v procesoru IA-64.  
  
 Pokud například potřebujete zadat #83 registru dat v procesoru IA-64, použijte `REGISTER_IA64_R0` příkaz + 83.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Ladění výčtů](debugging-enumerations.md)
