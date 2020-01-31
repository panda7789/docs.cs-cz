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
ms.openlocfilehash: 9f62d94d30c8c4f23073895b8ff0f7afa2dbad6b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792487"
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
 pro Hodnota výčtu [CorDebugJITCompilerFlags –](cordebugjitcompilerflags-enumeration.md) , která určuje příznaky kompilátoru používané pro výběr správné předem kompilované image.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `SetDesiredNGENCompilerFlags` Určuje příznaky, které musí být vloženy do předkompilované bitové kopie, aby modul runtime tento obrázek načetl do tohoto procesu. Příznaky nastavené touto metodou slouží pouze k výběru správné předkompilované image. Pokud taková image neexistuje, modul runtime místo toho načte obrázek jazyka MSIL (Microsoft Intermediate Language) a kompilátor JIT (just-in-time). V takovém případě musí ladicí program stále používat metodu [ICorDebugModule2:: SetJITCompilerFlags –](icordebugmodule2-setjitcompilerflags-method.md) k nastavení příznaků požadovaných pro kompilaci JIT.  
  
 Pokud je načtena bitová kopie, ale pro tuto bitovou kopii musí být provedeno některé kompilace JIT (což bude případ, pokud bitová kopie obsahuje obecné typy), budou příznaky kompilátoru zadané metodou `SetDesiredNGENCompilerFlags` platit pro další kompilaci JIT.  
  
 Metoda `SetDesiredNGENCompilerFlags` musí být volána během zpětného volání [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) . Pokusí se zavolat metodu `SetDesiredNGENCompilerFlags` poté selže. Také se pokusy o nastavení příznaků, které nejsou definovány ve výčtu `CorDebugJITCompilerFlags` nebo nejsou platné pro daný proces, se nezdaří.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebug – rozhraní](icordebug-interface.md)
- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
