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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75b28dafae2861a2d33363f95a46bf1abf4cda35
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756577"
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="7fa3f-102">ICorDebugILFrame::CanSetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="7fa3f-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="7fa3f-103">Získá HRESULT, která určuje, jestli je bezpečný pro nastavení ukazatele na instrukci do zadaného umístění posunu v kódu Microsoft Intermediate Language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="7fa3f-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fa3f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7fa3f-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fa3f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7fa3f-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="7fa3f-106">[in] Požadované nastavení pro ukazatele na instrukci.</span><span class="sxs-lookup"><span data-stu-id="7fa3f-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7fa3f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7fa3f-107">Remarks</span></span>  
 <span data-ttu-id="7fa3f-108">Použití `CanSetIP` před voláním metody [icordebugilframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="7fa3f-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="7fa3f-109">Pokud `CanSetIP` vrátí všechny HRESULT než S_OK, můžete stále vyvolat `ICorDebugILFrame::SetIP`, ale neexistuje žádná záruka, že ladicí program bude pokračovat v provádění bezpečné a správné kódu, který se právě ladí.</span><span class="sxs-lookup"><span data-stu-id="7fa3f-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fa3f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7fa3f-110">Requirements</span></span>  
 <span data-ttu-id="7fa3f-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fa3f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fa3f-112">**Záhlaví:** H CorDebug.idl, CorDebug,</span><span class="sxs-lookup"><span data-stu-id="7fa3f-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="7fa3f-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7fa3f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fa3f-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fa3f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
