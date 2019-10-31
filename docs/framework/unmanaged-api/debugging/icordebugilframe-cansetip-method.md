---
title: ICorDebugILFrame::CanSetIP – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
ms.openlocfilehash: 57d83d1f301cbfd43f8f553d9aef4beb3baf95f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131086"
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="98d13-102">ICorDebugILFrame::CanSetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="98d13-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="98d13-103">Získá hodnotu HRESULT, která označuje, zda je bezpečné nastavit ukazatel na instrukci na zadané místo posunutí v kódu jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="98d13-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98d13-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98d13-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98d13-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="98d13-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="98d13-106">pro Požadované nastavení pro ukazatel na instrukci.</span><span class="sxs-lookup"><span data-stu-id="98d13-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98d13-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="98d13-107">Remarks</span></span>  
 <span data-ttu-id="98d13-108">Před voláním metody [ICorDebugILFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) použijte metodu `CanSetIP`.</span><span class="sxs-lookup"><span data-stu-id="98d13-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="98d13-109">Pokud `CanSetIP` vrátí jakýkoli HRESULT jiný než S_OK, můžete přesto vyvolat `ICorDebugILFrame::SetIP`, ale není nijak zaručeno, že ladicí program bude pokračovat v bezpečném a správného spuštění kódu, který je právě laděn.</span><span class="sxs-lookup"><span data-stu-id="98d13-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98d13-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="98d13-110">Requirements</span></span>  
 <span data-ttu-id="98d13-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98d13-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98d13-112">**Hlavička:** CorDebug. idl, CorDebug, h</span><span class="sxs-lookup"><span data-stu-id="98d13-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="98d13-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="98d13-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98d13-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98d13-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
