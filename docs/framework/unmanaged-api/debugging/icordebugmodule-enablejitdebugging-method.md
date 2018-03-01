---
title: "ICorDebugModule::EnableJITDebugging – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7a699f32d8ec4b2418c6af815c22f35470bede3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="bef1a-102">ICorDebugModule::EnableJITDebugging – metoda</span><span class="sxs-lookup"><span data-stu-id="bef1a-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="bef1a-103">Určuje, zda kompilátoru za běhu (JIT) uchovává informace o ladění pro metod v rámci tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="bef1a-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bef1a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bef1a-104">Syntax</span></span>  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bef1a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bef1a-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="bef1a-106">[v] Nastavte hodnotu `true` povolení JIT kompilátoru zachovat informace o mapování mezi verze Microsoft (MSIL intermediate language) a verzí kompilována jednotlivých metod v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="bef1a-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="bef1a-107">[v] Nastavte hodnotu `true` povolení JIT kompilátoru pro generování kódu s určitým optimalizace JIT specifické pro ladění.</span><span class="sxs-lookup"><span data-stu-id="bef1a-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bef1a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bef1a-108">Remarks</span></span>  
 <span data-ttu-id="bef1a-109">Ve výchozím nastavení pro všechny moduly, které jsou načteny, když je aktivní ladicí program je povoleno ladění JIT.</span><span class="sxs-lookup"><span data-stu-id="bef1a-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="bef1a-110">Prostřednictvím kódu programu povolení nebo zakázání nastavení přepsání globální nastavení.</span><span class="sxs-lookup"><span data-stu-id="bef1a-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bef1a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bef1a-111">Requirements</span></span>  
 <span data-ttu-id="bef1a-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bef1a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bef1a-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bef1a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bef1a-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bef1a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bef1a-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bef1a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
