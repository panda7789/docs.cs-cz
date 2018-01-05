---
title: "ICorDebugILFrame::CanSetIP – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.CanSetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 22d0df9add0a4ce35b1a590d65e30a6756fec49c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="0eca2-102">ICorDebugILFrame::CanSetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="0eca2-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="0eca2-103">Získá HRESULT určující, zda je možné nastavit ukazatel instrukce do zadaného umístění posunu v kódu Microsoft Intermediate Language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="0eca2-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eca2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0eca2-104">Syntax</span></span>  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0eca2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0eca2-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="0eca2-106">[v] Ukazatel instrukce požadované nastavení.</span><span class="sxs-lookup"><span data-stu-id="0eca2-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0eca2-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0eca2-107">Remarks</span></span>  
 <span data-ttu-id="0eca2-108">Použití `CanSetIP` metoda před voláním [icordebugilframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="0eca2-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="0eca2-109">Pokud `CanSetIP` vrátí všechny HRESULT než S_OK, můžete stále vyvolat `ICorDebugILFrame::SetIP`, ale neexistuje žádná záruka, že bezpečné a správné spuštění kódu laděné bude pokračovat, ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="0eca2-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0eca2-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0eca2-110">Requirements</span></span>  
 <span data-ttu-id="0eca2-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0eca2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0eca2-112">**Záhlaví:** CorDebug.idl, CorDebug, h</span><span class="sxs-lookup"><span data-stu-id="0eca2-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="0eca2-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0eca2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0eca2-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0eca2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
