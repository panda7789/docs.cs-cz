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
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="7adfa-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="7adfa-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="7adfa-103">Nastaví příznaky, které musí být vloženy do předkompilovaných imagí, aby modul runtime tento obrázek načetl do aktuálního procesu.</span><span class="sxs-lookup"><span data-stu-id="7adfa-103">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7adfa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7adfa-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7adfa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7adfa-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="7adfa-106">pro Hodnota výčtu [CorDebugJITCompilerFlags –](cordebugjitcompilerflags-enumeration.md) , která určuje příznaky kompilátoru používané pro výběr správné předem kompilované image.</span><span class="sxs-lookup"><span data-stu-id="7adfa-106">[in] A value of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7adfa-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7adfa-107">Remarks</span></span>  
 <span data-ttu-id="7adfa-108">`SetDesiredNGENCompilerFlags`Metoda Určuje příznaky, které musí být vloženy do předkompilované bitové kopie, aby modul runtime tento obrázek načetl do tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="7adfa-108">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="7adfa-109">Příznaky nastavené touto metodou slouží pouze k výběru správné předkompilované image.</span><span class="sxs-lookup"><span data-stu-id="7adfa-109">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="7adfa-110">Pokud taková image neexistuje, modul runtime místo toho načte obrázek jazyka MSIL (Microsoft Intermediate Language) a kompilátor JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="7adfa-110">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="7adfa-111">V takovém případě musí ladicí program stále používat metodu [ICorDebugModule2:: SetJITCompilerFlags –](icordebugmodule2-setjitcompilerflags-method.md) k nastavení příznaků požadovaných pro kompilaci JIT.</span><span class="sxs-lookup"><span data-stu-id="7adfa-111">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="7adfa-112">Pokud je načtena bitová kopie, ale některé kompilace JIT musí probíhat pro tuto bitovou kopii (což bude případ, pokud bitová kopie obsahuje obecné typy), budou příznaky kompilátoru zadané `SetDesiredNGENCompilerFlags` metodou platit pro další KOMPILACI JIT.</span><span class="sxs-lookup"><span data-stu-id="7adfa-112">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="7adfa-113">`SetDesiredNGENCompilerFlags`Metoda musí být volána během zpětného volání [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7adfa-113">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="7adfa-114">Pokusí se zavolat `SetDesiredNGENCompilerFlags` metodu následně selže.</span><span class="sxs-lookup"><span data-stu-id="7adfa-114">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="7adfa-115">Také se pokusy o nastavování příznaků, které nejsou definovány ve `CorDebugJITCompilerFlags` výčtu nebo nejsou pro daný proces platné, se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="7adfa-115">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7adfa-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7adfa-116">Requirements</span></span>  
 <span data-ttu-id="7adfa-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7adfa-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7adfa-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7adfa-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7adfa-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7adfa-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7adfa-120">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7adfa-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7adfa-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="7adfa-121">See also</span></span>

- [<span data-ttu-id="7adfa-122">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7adfa-122">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="7adfa-123">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7adfa-123">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
