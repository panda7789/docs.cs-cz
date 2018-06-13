---
title: ICorDebugChain::GetStackRange – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 226f8c431b90d53366aa5e504101e7de581ec570
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402467"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="dddea-102">ICorDebugChain::GetStackRange – metoda</span><span class="sxs-lookup"><span data-stu-id="dddea-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="dddea-103">Získá rozsah adres segmentu zásobníku pro tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="dddea-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dddea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dddea-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dddea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dddea-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="dddea-106">[out] Ukazatel na `CORDB_ADDRESS` hodnotu, která je počáteční adresa segmentu zásobníku.</span><span class="sxs-lookup"><span data-stu-id="dddea-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="dddea-107">[out] Ukazatel na `CORDB_ADDRESS` hodnotu, která je koncová adresa segmentu zásobníku.</span><span class="sxs-lookup"><span data-stu-id="dddea-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dddea-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dddea-108">Remarks</span></span>  
 <span data-ttu-id="dddea-109">Číselný rozsah má smysl pouze pro porovnání umístění rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="dddea-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="dddea-110">Nelze vytvořit žádný odhad o tom, co je ve skutečnosti uloženy v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="dddea-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dddea-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dddea-111">Requirements</span></span>  
 <span data-ttu-id="dddea-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dddea-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dddea-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dddea-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dddea-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dddea-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dddea-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dddea-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
