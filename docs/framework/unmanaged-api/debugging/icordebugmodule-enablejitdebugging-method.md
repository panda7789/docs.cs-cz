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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71722293bfb80a7e57393916560f922d970ea2ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415639"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="2b9c9-102">ICorDebugModule::EnableJITDebugging – metoda</span><span class="sxs-lookup"><span data-stu-id="2b9c9-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="2b9c9-103">Určuje, zda kompilátoru za běhu (JIT) uchovává informace o ladění pro metod v rámci tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="2b9c9-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b9c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b9c9-104">Syntax</span></span>  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b9c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b9c9-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="2b9c9-106">[v] Nastavte hodnotu `true` povolení JIT kompilátoru zachovat informace o mapování mezi verze Microsoft (MSIL intermediate language) a verzí kompilována jednotlivých metod v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="2b9c9-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="2b9c9-107">[v] Nastavte hodnotu `true` povolení JIT kompilátoru pro generování kódu s určitým optimalizace JIT specifické pro ladění.</span><span class="sxs-lookup"><span data-stu-id="2b9c9-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b9c9-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b9c9-108">Remarks</span></span>  
 <span data-ttu-id="2b9c9-109">Ve výchozím nastavení pro všechny moduly, které jsou načteny, když je aktivní ladicí program je povoleno ladění JIT.</span><span class="sxs-lookup"><span data-stu-id="2b9c9-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="2b9c9-110">Prostřednictvím kódu programu povolení nebo zakázání nastavení přepsání globální nastavení.</span><span class="sxs-lookup"><span data-stu-id="2b9c9-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b9c9-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b9c9-111">Requirements</span></span>  
 <span data-ttu-id="2b9c9-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b9c9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b9c9-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b9c9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b9c9-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b9c9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b9c9-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b9c9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
