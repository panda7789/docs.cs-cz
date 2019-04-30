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
ms.openlocfilehash: 642c4fd600d10ef89a08aa32bef5c8e7455552c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937173"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="ffe75-102">ICorDebugModule::EnableJITDebugging – metoda</span><span class="sxs-lookup"><span data-stu-id="ffe75-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="ffe75-103">Určuje, zda kompilátor just-in-time (JIT) uchovává informace o ladění pro metody v rámci tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="ffe75-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffe75-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ffe75-104">Syntax</span></span>  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffe75-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ffe75-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="ffe75-106">[in] Nastavte tuto hodnotu na `true` umožňující kompilátor JIT pro zachování informací o mapování mezi Microsoft intermediate language (MSIL) verze a verze zkompilovaný pomocí kompilátoru JIT jednotlivých metod v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="ffe75-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="ffe75-107">[in] Nastavte tuto hodnotu na `true` umožňující kompilátor JIT pro generování kódu pomocí některé optimalizace JIT specifické pro ladění.</span><span class="sxs-lookup"><span data-stu-id="ffe75-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffe75-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ffe75-108">Remarks</span></span>  
 <span data-ttu-id="ffe75-109">Ve výchozím nastavení pro všechny moduly, které jsou načteny, když je aktivní ladicí program je povoleno ladění JIT.</span><span class="sxs-lookup"><span data-stu-id="ffe75-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="ffe75-110">Programově povolení nebo zakázání nastavení přepíše globální nastavení.</span><span class="sxs-lookup"><span data-stu-id="ffe75-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffe75-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ffe75-111">Requirements</span></span>  
 <span data-ttu-id="ffe75-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffe75-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffe75-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ffe75-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ffe75-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ffe75-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffe75-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffe75-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
