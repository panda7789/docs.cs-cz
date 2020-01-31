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
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="13bd7-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="13bd7-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="13bd7-103">Nastaví příznaky, které musí být vloženy do předkompilovaných imagí, aby modul runtime tento obrázek načetl do aktuálního procesu.</span><span class="sxs-lookup"><span data-stu-id="13bd7-103">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13bd7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13bd7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13bd7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="13bd7-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="13bd7-106">pro Hodnota výčtu [CorDebugJITCompilerFlags –](cordebugjitcompilerflags-enumeration.md) , která určuje příznaky kompilátoru používané pro výběr správné předem kompilované image.</span><span class="sxs-lookup"><span data-stu-id="13bd7-106">[in] A value of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13bd7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13bd7-107">Remarks</span></span>  
 <span data-ttu-id="13bd7-108">Metoda `SetDesiredNGENCompilerFlags` Určuje příznaky, které musí být vloženy do předkompilované bitové kopie, aby modul runtime tento obrázek načetl do tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="13bd7-108">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="13bd7-109">Příznaky nastavené touto metodou slouží pouze k výběru správné předkompilované image.</span><span class="sxs-lookup"><span data-stu-id="13bd7-109">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="13bd7-110">Pokud taková image neexistuje, modul runtime místo toho načte obrázek jazyka MSIL (Microsoft Intermediate Language) a kompilátor JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="13bd7-110">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="13bd7-111">V takovém případě musí ladicí program stále používat metodu [ICorDebugModule2:: SetJITCompilerFlags –](icordebugmodule2-setjitcompilerflags-method.md) k nastavení příznaků požadovaných pro kompilaci JIT.</span><span class="sxs-lookup"><span data-stu-id="13bd7-111">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="13bd7-112">Pokud je načtena bitová kopie, ale pro tuto bitovou kopii musí být provedeno některé kompilace JIT (což bude případ, pokud bitová kopie obsahuje obecné typy), budou příznaky kompilátoru zadané metodou `SetDesiredNGENCompilerFlags` platit pro další kompilaci JIT.</span><span class="sxs-lookup"><span data-stu-id="13bd7-112">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="13bd7-113">Metoda `SetDesiredNGENCompilerFlags` musí být volána během zpětného volání [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="13bd7-113">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="13bd7-114">Pokusí se zavolat metodu `SetDesiredNGENCompilerFlags` poté selže.</span><span class="sxs-lookup"><span data-stu-id="13bd7-114">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="13bd7-115">Také se pokusy o nastavení příznaků, které nejsou definovány ve výčtu `CorDebugJITCompilerFlags` nebo nejsou platné pro daný proces, se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="13bd7-115">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13bd7-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="13bd7-116">Requirements</span></span>  
 <span data-ttu-id="13bd7-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13bd7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13bd7-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="13bd7-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13bd7-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="13bd7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13bd7-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13bd7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13bd7-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13bd7-121">See also</span></span>

- [<span data-ttu-id="13bd7-122">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="13bd7-122">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="13bd7-123">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="13bd7-123">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
