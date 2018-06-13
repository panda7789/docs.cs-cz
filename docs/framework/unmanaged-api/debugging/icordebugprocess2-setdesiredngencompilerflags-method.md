---
title: ICorDebugProcess2::SetDesiredNGENCompilerFlags – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94ba2b0cf7d88104eaadd434732edf3c1d4060e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422698"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a>ICorDebugProcess2::SetDesiredNGENCompilerFlags – metoda
Nastaví příznaky, které je třeba myslet ve předkompilovaných bitové kopie v pořadí pro modul runtime k načtení této bitové kopie do aktuální proces.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwFlags`  
 [v] Hodnota [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) výčet, který určuje příznaky kompilátoru použit k výběru správné předem kompilovaném bitové kopie.  
  
## <a name="remarks"></a>Poznámky  
 `SetDesiredNGENCompilerFlags` Metoda určuje příznaky, které je třeba myslet ve předkompilovaných obrázku tak, aby modul runtime načte této bitové kopie do tohoto procesu. Příznaky nastavit touto metodou se používají jenom k výběru správné předkompilovaných bitové kopie. Pokud žádný takový obrázek existuje, modul runtime načíst obrázek (MSIL intermediate language) společnosti Microsoft a kompilátoru za běhu (JIT) namísto toho. V takovém případě musíte dál používat ladicí program [icordebugmodule2::setjitcompilerflags –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) metoda nastavit příznaky podle potřeby JIT kompilace.  
  
 Pokud bitovou kopii je načtena, ale některé JIT kompilace musí proběhnout obrázku (který bude v případě, pokud bitová kopie obsahuje obecné typy), příznaky kompilátoru určeného `SetDesiredNGENCompilerFlags` metoda se použijí na navíc JIT – kompilace.  
  
 `SetDesiredNGENCompilerFlags` Metoda musí být volána v průběhu [icordebugmanagedcallback::CreateProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) zpětného volání. Pokusí se volání `SetDesiredNGENCompilerFlags` metoda později selže. Rovněž, pokusí se nastavit příznaky, které jsou buď není definovaný v `CorDebugJITCompilerFlags` výčtu nebo jsou právní není pro daný proces se nezdaří.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
