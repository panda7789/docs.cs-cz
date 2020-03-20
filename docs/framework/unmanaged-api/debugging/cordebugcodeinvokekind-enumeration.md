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
ms.openlocfilehash: 54332f5b3383f1c1513242a79cbd81eb8aa5c4f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179250"
---
# <a name="cordebugcodeinvokekind-enumeration"></a>Výčet CorDebugCodeInvokeKind
Popisuje, jak exportovaná funkce vyvolá spravovaný kód.  
  
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
|`CODE_INVOKE_KIND_NONE`|Pokud je touto metodou vyvolán jakýkoli spravovaný kód, bude muset být později umístěn explicitními událostmi nebo zarážkymi.<br /><br /> ...nebo--<br /><br /> Můžeme jen chybět některé spravovaného kódu, který tato metoda volá, protože neexistuje žádný snadný způsob, jak na něm zastavit.<br /><br /> ...nebo--<br /><br /> Metoda může nikdy vyvolat spravovaný kód.|  
|`CODE_INVOKE_KIND_RETURN`|Tato metoda vyvolá spravovaný kód prostřednictvím instrukce vrácení. Krokování by mělo být doručeno k dalšímu spravovanému kódu.|  
|`CODE_INVOKE_KIND_TAILCALL`|Tato metoda vyvolá spravovaný kód prostřednictvím volání ocasu. Jednokrokování a krokování přes všechny pokyny k volání by měly dorazit ke spravovanému kódu.|  
  
## <a name="remarks"></a>Poznámky  
 Tento výčet používá metoda [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) k poskytnutí informací o krokování spravovaného kódu.  
  
> [!NOTE]
> Tento výčet je určen pouze pro použití v nativních scénářích ladění .NET.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro ladění](debugging-enumerations.md)
- [ladění](index.md)
