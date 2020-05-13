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
ms.openlocfilehash: 366a48e5f6abd92f0c6f796f40bdd263181da4a8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213475"
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
 `SetDesiredNGENCompilerFlags`Metoda Určuje příznaky, které musí být vloženy do předkompilované bitové kopie, aby modul runtime tento obrázek načetl do tohoto procesu. Příznaky nastavené touto metodou slouží pouze k výběru správné předkompilované image. Pokud taková image neexistuje, modul runtime místo toho načte obrázek jazyka MSIL (Microsoft Intermediate Language) a kompilátor JIT (just-in-time). V takovém případě musí ladicí program stále používat metodu [ICorDebugModule2:: SetJITCompilerFlags –](icordebugmodule2-setjitcompilerflags-method.md) k nastavení příznaků požadovaných pro kompilaci JIT.  
  
 Pokud je načtena bitová kopie, ale některé kompilace JIT musí probíhat pro tuto bitovou kopii (což bude případ, pokud bitová kopie obsahuje obecné typy), budou příznaky kompilátoru zadané `SetDesiredNGENCompilerFlags` metodou platit pro další KOMPILACI JIT.  
  
 `SetDesiredNGENCompilerFlags`Metoda musí být volána během zpětného volání [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) . Pokusí se zavolat `SetDesiredNGENCompilerFlags` metodu následně selže. Také se pokusy o nastavování příznaků, které nejsou definovány ve `CorDebugJITCompilerFlags` výčtu nebo nejsou pro daný proces platné, se nezdaří.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebug – rozhraní](icordebug-interface.md)
- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
