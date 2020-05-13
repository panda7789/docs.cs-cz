---
title: ICorDebugModule::EnableJITDebugging – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableJITDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type:
- apiref
ms.openlocfilehash: bdf027f94c8416d052cb807d04be76a39868ccf7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212929"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="e3000-102">ICorDebugModule::EnableJITDebugging – metoda</span><span class="sxs-lookup"><span data-stu-id="e3000-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="e3000-103">Určuje, zda kompilátor JIT (just-in-time) zachovává ladicí informace pro metody v rámci tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="e3000-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3000-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3000-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3000-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3000-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="e3000-106">pro Nastavte tuto hodnotu, chcete-li `true` Povolit kompilátoru JIT zachovat informace o mapování mezi verzí jazyka MSIL (Microsoft Intermediate Language) a verzí zkompilované kompilátorem JIT pro každou metodu v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="e3000-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="e3000-107">pro Nastavte tuto hodnotu na `true` , pokud chcete, aby kompilátor JIT vygeneroval kód s některými optimalizacemi specifickými pro JIT pro ladění.</span><span class="sxs-lookup"><span data-stu-id="e3000-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3000-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e3000-108">Remarks</span></span>  
 <span data-ttu-id="e3000-109">Ladění JIT je ve výchozím nastavení povoleno pro všechny moduly, které jsou načteny, když je ladicí program aktivní.</span><span class="sxs-lookup"><span data-stu-id="e3000-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="e3000-110">Programové povolení nebo zakázání nastavení přepisuje globální nastavení.</span><span class="sxs-lookup"><span data-stu-id="e3000-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3000-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e3000-111">Requirements</span></span>  
 <span data-ttu-id="e3000-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3000-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3000-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e3000-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3000-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e3000-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3000-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3000-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
