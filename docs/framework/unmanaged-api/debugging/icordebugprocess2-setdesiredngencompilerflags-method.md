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
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="a695f-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="a695f-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="a695f-103">Nastaví příznaky, které je třeba myslet ve předkompilovaných bitové kopie v pořadí pro modul runtime k načtení této bitové kopie do aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="a695f-103">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a695f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a695f-104">Syntax</span></span>  
  
```  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a695f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a695f-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="a695f-106">[v] Hodnota [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) výčet, který určuje příznaky kompilátoru použit k výběru správné předem kompilovaném bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="a695f-106">[in] A value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a695f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a695f-107">Remarks</span></span>  
 <span data-ttu-id="a695f-108">`SetDesiredNGENCompilerFlags` Metoda určuje příznaky, které je třeba myslet ve předkompilovaných obrázku tak, aby modul runtime načte této bitové kopie do tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="a695f-108">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="a695f-109">Příznaky nastavit touto metodou se používají jenom k výběru správné předkompilovaných bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="a695f-109">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="a695f-110">Pokud žádný takový obrázek existuje, modul runtime načíst obrázek (MSIL intermediate language) společnosti Microsoft a kompilátoru za běhu (JIT) namísto toho.</span><span class="sxs-lookup"><span data-stu-id="a695f-110">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="a695f-111">V takovém případě musíte dál používat ladicí program [icordebugmodule2::setjitcompilerflags –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) metoda nastavit příznaky podle potřeby JIT kompilace.</span><span class="sxs-lookup"><span data-stu-id="a695f-111">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="a695f-112">Pokud bitovou kopii je načtena, ale některé JIT kompilace musí proběhnout obrázku (který bude v případě, pokud bitová kopie obsahuje obecné typy), příznaky kompilátoru určeného `SetDesiredNGENCompilerFlags` metoda se použijí na navíc JIT – kompilace.</span><span class="sxs-lookup"><span data-stu-id="a695f-112">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="a695f-113">`SetDesiredNGENCompilerFlags` Metoda musí být volána v průběhu [icordebugmanagedcallback::CreateProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="a695f-113">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="a695f-114">Pokusí se volání `SetDesiredNGENCompilerFlags` metoda později selže.</span><span class="sxs-lookup"><span data-stu-id="a695f-114">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="a695f-115">Rovněž, pokusí se nastavit příznaky, které jsou buď není definovaný v `CorDebugJITCompilerFlags` výčtu nebo jsou právní není pro daný proces se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="a695f-115">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a695f-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a695f-116">Requirements</span></span>  
 <span data-ttu-id="a695f-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a695f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a695f-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a695f-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a695f-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a695f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a695f-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a695f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a695f-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="a695f-121">See Also</span></span>  
 [<span data-ttu-id="a695f-122">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a695f-122">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="a695f-123">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a695f-123">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
