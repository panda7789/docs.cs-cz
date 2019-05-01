---
title: ICorDebugFunction2::GetJMCStatus – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d23a0a489cfe13201b7798920feb3528db3b0709
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988660"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="874d3-102">ICorDebugFunction2::GetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="874d3-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="874d3-103">Získá hodnotu, která indikuje, jestli je funkce, která je reprezentována tímto objektem icordebugfunction2 – označený jako uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="874d3-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="874d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="874d3-104">Syntax</span></span>  
  
```  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="874d3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="874d3-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="874d3-106">[out] Ukazatel na logickou hodnotu, která je `true`, pokud se tato funkce je označená jako uživatelského kódu; v opačném případě hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="874d3-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="874d3-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="874d3-107">Remarks</span></span>  
 <span data-ttu-id="874d3-108">Pokud funkci představovaného tímto rozhraním `ICorDebugFunction2` nejde ladit, `pbIsJustMyCode` bude vždy `false`.</span><span class="sxs-lookup"><span data-stu-id="874d3-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="874d3-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="874d3-109">Requirements</span></span>  
 <span data-ttu-id="874d3-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="874d3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="874d3-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="874d3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="874d3-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="874d3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="874d3-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="874d3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
