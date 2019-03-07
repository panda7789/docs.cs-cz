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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93a8c8650822c5d986e21a456d58b2dc0327f05b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479517"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="a74a9-102">ICorDebugNativeFrame::CanSetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="a74a9-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="a74a9-103">Získá HRESULT, která určuje, jestli je bezpečný pro nastavení ukazatele instrukce (IP) do zadaného umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="a74a9-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a74a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a74a9-104">Syntax</span></span>  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a74a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a74a9-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="a74a9-106">[in] Požadované nastavení pro ukazatele na instrukci.</span><span class="sxs-lookup"><span data-stu-id="a74a9-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a74a9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a74a9-107">Remarks</span></span>  
 <span data-ttu-id="a74a9-108">Použití `CanSetIP` před voláním metody [icordebugnativeframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a74a9-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="a74a9-109">Pokud `CanSetIP` vrátí všechny HRESULT než S_OK, můžete stále vyvolat `ICorDebugNativeFrame::SetIP`, ale neexistuje žádná záruka, že ladicí program bude pokračovat v provádění bezpečné a správné kódu, který se právě ladí.</span><span class="sxs-lookup"><span data-stu-id="a74a9-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a74a9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a74a9-110">Requirements</span></span>  
 <span data-ttu-id="a74a9-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a74a9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a74a9-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a74a9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a74a9-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a74a9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a74a9-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a74a9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a74a9-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a74a9-115">See also</span></span>

