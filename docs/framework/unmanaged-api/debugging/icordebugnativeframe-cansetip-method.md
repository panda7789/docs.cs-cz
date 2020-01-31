---
title: ICorDebugNativeFrame::CanSetIP – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
ms.openlocfilehash: d266ec7f82d7d4c7c66f137aafc1c8865d6f8889
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792806"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="04049-102">ICorDebugNativeFrame::CanSetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="04049-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="04049-103">Získá hodnotu HRESULT, která označuje, zda je bezpečné nastavit ukazatel na instrukce (IP) na zadané umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="04049-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04049-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04049-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04049-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04049-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="04049-106">pro Požadované nastavení pro ukazatel na instrukci.</span><span class="sxs-lookup"><span data-stu-id="04049-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04049-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04049-107">Remarks</span></span>  
 <span data-ttu-id="04049-108">Použijte metodu `CanSetIP` před voláním metody [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md) .</span><span class="sxs-lookup"><span data-stu-id="04049-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="04049-109">Pokud `CanSetIP` vrátí jakýkoli HRESULT jiný než S_OK, můžete přesto vyvolat `ICorDebugNativeFrame::SetIP`, ale není nijak zaručeno, že ladicí program bude pokračovat v bezpečném a správném spuštění kódu, který je právě laděn.</span><span class="sxs-lookup"><span data-stu-id="04049-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04049-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04049-110">Requirements</span></span>  
 <span data-ttu-id="04049-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04049-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04049-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="04049-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04049-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="04049-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04049-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04049-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04049-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04049-115">See also</span></span>
