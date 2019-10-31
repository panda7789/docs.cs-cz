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
ms.openlocfilehash: 9313fc58dec8099f42dbff07685ca14791fa324f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137166"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a>ICorDebugProcess2::SetDesiredNGENCompilerFlags – metoda
Nastaví příznaky, které musí být vloženy do předkompilovaných imagí, aby modul runtime tento obrázek načetl do aktuálního procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwFlags`  
 pro Hodnota výčtu [CorDebugJITCompilerFlags –](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) , která určuje příznaky kompilátoru používané pro výběr správné předem kompilované image.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `SetDesiredNGENCompilerFlags` Určuje příznaky, které musí být vloženy do předkompilované bitové kopie, aby modul runtime tento obrázek načetl do tohoto procesu. Příznaky nastavené touto metodou slouží pouze k výběru správné předkompilované image. Pokud taková image neexistuje, modul runtime místo toho načte obrázek jazyka MSIL (Microsoft Intermediate Language) a kompilátor JIT (just-in-time). V takovém případě musí ladicí program stále používat metodu [ICorDebugModule2:: SetJITCompilerFlags –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) k nastavení příznaků požadovaných pro kompilaci JIT.  
  
 Pokud je načtena bitová kopie, ale pro tuto bitovou kopii musí být provedeno některé kompilace JIT (což bude případ, pokud bitová kopie obsahuje obecné typy), budou příznaky kompilátoru zadané metodou `SetDesiredNGENCompilerFlags` platit pro další kompilaci JIT.  
  
 Metoda `SetDesiredNGENCompilerFlags` musí být volána během zpětného volání [ICorDebugManagedCallback:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) . Pokusí se zavolat metodu `SetDesiredNGENCompilerFlags` poté selže. Také se pokusy o nastavení příznaků, které nejsou definovány ve výčtu `CorDebugJITCompilerFlags` nebo nejsou platné pro daný proces, se nezdaří.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
