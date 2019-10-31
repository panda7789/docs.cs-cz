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
ms.openlocfilehash: cc839e9b2a28dc428ae7cc87c9d080c4b7612a9d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098883"
---
# <a name="cordebugcodeinvokekind-enumeration"></a>Výčet CorDebugCodeInvokeKind
Popisuje, jak exportovaný funkce vyvolá spravovaný kód.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
|`CODE_INVOKE_KIND_NONE`|Pokud je v této metodě vyvolán nějaký spravovaný kód, bude muset být umístěn pomocí explicitních událostí nebo zarážek později.<br /><br /> --nebo--<br /><br /> Omlouváme se, ale může se stát, že tato metoda volá jenom některé spravované kódy, protože neexistuje žádný snadný způsob, jak ji zastavit.<br /><br /> --nebo--<br /><br /> Metoda nikdy nemůže vyvolat spravovaný kód.|  
|`CODE_INVOKE_KIND_RETURN`|Tato metoda vyvolá spravovaný kód prostřednictvím návratové instrukce. Krokování by mělo být doručeno do dalšího spravovaného kódu.|  
|`CODE_INVOKE_KIND_TAILCALL`|Tato metoda vyvolá spravovaný kód prostřednictvím volání tail. Do spravovaného kódu by měly být doručeny jednoduché krokování a krokování prostřednictvím jakýchkoli instrukcí volání.|  
  
## <a name="remarks"></a>Poznámky  
 Tento výčet používá metoda [ICorDebugProcess6:: GetExportStepInfo –](icordebugprocess6-getexportstepinfo-method.md) k poskytnutí informací o prokrokování prostřednictvím spravovaného kódu.  
  
> [!NOTE]
> Tento výčet je určený pro použití pouze v .NET Nativech scénářích ladění.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](debugging-enumerations.md)
- [Ladění](index.md)
