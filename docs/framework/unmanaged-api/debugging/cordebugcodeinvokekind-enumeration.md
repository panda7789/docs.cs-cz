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
ms.openlocfilehash: b3b4906f988d09f7b01aee40e8f63b589da5f33d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609201"
---
# <a name="cordebugcodeinvokekind-enumeration"></a>Výčet CorDebugCodeInvokeKind
Popisuje, jak exportované funkce volá spravovaný kód.  
  
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
|`CODE_INVOKE_KIND_NONE`|Pokud spravovaný kód vyvolá tuto metodu, bude mít umístěné explicitní události nebo zarážek později.<br /><br /> --nebo--<br /><br /> Jsme právě přijít o některé spravovaný kód, který tato metoda se volá, protože neexistuje žádný snadný způsob, jak zastavit na něj.<br /><br /> --nebo--<br /><br /> Spravovaný kód může nikdy vyvolání metody.|  
|`CODE_INVOKE_KIND_RETURN`|Tato metoda vyvolá spravovaný kód prostřednictvím návratový instrukce. Krokování by měl přejít na další spravovaného kódu.|  
|`CODE_INVOKE_KIND_TAILCALL`|Tato metoda vyvolá spravovaného kódu pomocí volání funkce tail. Krokování jednou a krokování přes všechny pokyny volání by měl přejít na spravovaný kód.|  
  
## <a name="remarks"></a>Poznámky  
 Tento výčet je používán [icordebugprocess6::getexportstepinfo –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) metodu k dispozici informace o procházení spravovaného kódu.  
  
> [!NOTE]
>  Tento výčet je určena pro použití v .NET Native ladění pouze scénáře.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
