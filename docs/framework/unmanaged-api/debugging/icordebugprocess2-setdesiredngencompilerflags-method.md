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
ms.openlocfilehash: e061c3f3dc95e63339d6fd5f82b3cb4d38a4b6c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948821"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a>ICorDebugProcess2::SetDesiredNGENCompilerFlags – metoda
Nastaví příznaky, které musí být vložen do předkompilované bitové kopie v pořadí pro modul runtime k načtení této bitové kopie do aktuální proces.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwFlags`  
 [in] Hodnota [cordebugjitcompilerflags –](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) výčet, který určuje příznaky kompilátoru použity k výběru správné předem kompilovaných bitové kopie.  
  
## <a name="remarks"></a>Poznámky  
 `SetDesiredNGENCompilerFlags` Metody určuje příznaky, které musí být vložen do předkompilované image tak, aby modul runtime bude načtení této bitové kopie do tohoto procesu. Příznaky nastavením Tato metoda slouží jenom k výběru správné předkompilované bitové kopie. Pokud neexistuje žádný takový obrázek, modul runtime načíst image Microsoft intermediate language (MSIL) a kompilátor just-in-time (JIT) místo toho. V takovém případě musíte dál používat ladicí program [icordebugmodule2::setjitcompilerflags –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) metoda podle potřeby pro kompilaci JIT nastavit příznaky.  
  
 Pokud je obrázek načten, ale některé JIT kompilaci musí proběhnout obrázku (což bude v případě, pokud image obsahuje obecné typy), příznaky kompilátoru určené `SetDesiredNGENCompilerFlags` metoda má platit pro další kompilace JIT.  
  
 `SetDesiredNGENCompilerFlags` Metoda musí být volána v průběhu [icordebugmanagedcallback::CreateProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) zpětného volání. Pokusí se volání `SetDesiredNGENCompilerFlags` metoda později selžou. Také, pokusí se nastavit příznaky, které jsou buď není definován v `CorDebugJITCompilerFlags` výčet nebo jsou není platný pro daný proces se nezdaří.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
