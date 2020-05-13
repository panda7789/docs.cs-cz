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
ms.openlocfilehash: 2bd4ab4a080461c56b0287d24aa288847445d803
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210316"
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="37683-102">ICorDebugILFrame::CanSetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="37683-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="37683-103">Získá hodnotu HRESULT, která označuje, zda je bezpečné nastavit ukazatel na instrukci na zadané místo posunutí v kódu jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="37683-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37683-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37683-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37683-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37683-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="37683-106">pro Požadované nastavení pro ukazatel na instrukci.</span><span class="sxs-lookup"><span data-stu-id="37683-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37683-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37683-107">Remarks</span></span>  
 <span data-ttu-id="37683-108">Použijte `CanSetIP` metodu před voláním metody [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) .</span><span class="sxs-lookup"><span data-stu-id="37683-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="37683-109">Pokud `CanSetIP` vrátí hodnotu HRESULT jinou než S_OK, můžete stále vyvolat `ICorDebugILFrame::SetIP` , ale není nijak zaručeno, že ladicí program bude pokračovat v bezpečném a správného spuštění kódu, který je laděn.</span><span class="sxs-lookup"><span data-stu-id="37683-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37683-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37683-110">Requirements</span></span>  
 <span data-ttu-id="37683-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37683-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37683-112">**Hlavička:** CorDebug. idl, CorDebug, h</span><span class="sxs-lookup"><span data-stu-id="37683-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="37683-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="37683-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37683-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37683-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
