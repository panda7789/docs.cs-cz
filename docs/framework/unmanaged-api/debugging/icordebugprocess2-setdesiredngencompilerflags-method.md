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
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="a63e8-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="a63e8-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="a63e8-103">Nastaví příznaky, které musí být vložen do předkompilované bitové kopie v pořadí pro modul runtime k načtení této bitové kopie do aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="a63e8-103">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a63e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a63e8-104">Syntax</span></span>  
  
```  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a63e8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a63e8-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="a63e8-106">[in] Hodnota [cordebugjitcompilerflags –](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) výčet, který určuje příznaky kompilátoru použity k výběru správné předem kompilovaných bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="a63e8-106">[in] A value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a63e8-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a63e8-107">Remarks</span></span>  
 <span data-ttu-id="a63e8-108">`SetDesiredNGENCompilerFlags` Metody určuje příznaky, které musí být vložen do předkompilované image tak, aby modul runtime bude načtení této bitové kopie do tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="a63e8-108">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="a63e8-109">Příznaky nastavením Tato metoda slouží jenom k výběru správné předkompilované bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="a63e8-109">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="a63e8-110">Pokud neexistuje žádný takový obrázek, modul runtime načíst image Microsoft intermediate language (MSIL) a kompilátor just-in-time (JIT) místo toho.</span><span class="sxs-lookup"><span data-stu-id="a63e8-110">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="a63e8-111">V takovém případě musíte dál používat ladicí program [icordebugmodule2::setjitcompilerflags –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) metoda podle potřeby pro kompilaci JIT nastavit příznaky.</span><span class="sxs-lookup"><span data-stu-id="a63e8-111">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="a63e8-112">Pokud je obrázek načten, ale některé JIT kompilaci musí proběhnout obrázku (což bude v případě, pokud image obsahuje obecné typy), příznaky kompilátoru určené `SetDesiredNGENCompilerFlags` metoda má platit pro další kompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="a63e8-112">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="a63e8-113">`SetDesiredNGENCompilerFlags` Metoda musí být volána v průběhu [icordebugmanagedcallback::CreateProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="a63e8-113">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="a63e8-114">Pokusí se volání `SetDesiredNGENCompilerFlags` metoda později selžou.</span><span class="sxs-lookup"><span data-stu-id="a63e8-114">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="a63e8-115">Také, pokusí se nastavit příznaky, které jsou buď není definován v `CorDebugJITCompilerFlags` výčet nebo jsou není platný pro daný proces se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="a63e8-115">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a63e8-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a63e8-116">Requirements</span></span>  
 <span data-ttu-id="a63e8-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a63e8-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a63e8-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a63e8-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a63e8-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a63e8-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a63e8-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a63e8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a63e8-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a63e8-121">See also</span></span>

- [<span data-ttu-id="a63e8-122">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a63e8-122">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="a63e8-123">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a63e8-123">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
