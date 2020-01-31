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
ms.openlocfilehash: c6a02b080739d00667893008be4a19b4fa9a6ef2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788596"
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="4424d-102">ICorDebugILFrame::CanSetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="4424d-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="4424d-103">Získá hodnotu HRESULT, která označuje, zda je bezpečné nastavit ukazatel na instrukci na zadané místo posunutí v kódu jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="4424d-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4424d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4424d-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4424d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4424d-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="4424d-106">pro Požadované nastavení pro ukazatel na instrukci.</span><span class="sxs-lookup"><span data-stu-id="4424d-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4424d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4424d-107">Remarks</span></span>  
 <span data-ttu-id="4424d-108">Před voláním metody [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) použijte metodu `CanSetIP`.</span><span class="sxs-lookup"><span data-stu-id="4424d-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="4424d-109">Pokud `CanSetIP` vrátí jakýkoli HRESULT jiný než S_OK, můžete přesto vyvolat `ICorDebugILFrame::SetIP`, ale není nijak zaručeno, že ladicí program bude pokračovat v bezpečném a správném spuštění kódu, který je právě laděn.</span><span class="sxs-lookup"><span data-stu-id="4424d-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4424d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4424d-110">Requirements</span></span>  
 <span data-ttu-id="4424d-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4424d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4424d-112">**Hlavička:** CorDebug. idl, CorDebug, h</span><span class="sxs-lookup"><span data-stu-id="4424d-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="4424d-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4424d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4424d-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4424d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
