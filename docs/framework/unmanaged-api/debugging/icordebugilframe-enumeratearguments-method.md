---
title: ICorDebugILFrame::EnumerateArguments – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateArguments
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type:
- apiref
ms.openlocfilehash: 3945b1dea62dc0616d669356faf60f0d09cfb084
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210301"
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="4d47d-102">ICorDebugILFrame::EnumerateArguments – metoda</span><span class="sxs-lookup"><span data-stu-id="4d47d-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="4d47d-103">Získá enumerátor pro argumenty v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="4d47d-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d47d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d47d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d47d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d47d-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="4d47d-106">mimo Ukazatel na adresu objektu ICorDebugValueEnum, který je enumerátorem pro argumenty v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="4d47d-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d47d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d47d-107">Remarks</span></span>  
 <span data-ttu-id="4d47d-108">`EnumerateArguments`Získá enumerátor, který může vypsat argumenty, které jsou k dispozici v rámci volání, reprezentované tímto objektem ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="4d47d-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="4d47d-109">Seznam bude obsahovat argumenty, které jsou [vararg](/cpp/windows/vararg) (tj. proměnný počet argumentů), i argumenty, které nejsou `vararg` .</span><span class="sxs-lookup"><span data-stu-id="4d47d-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d47d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d47d-110">Requirements</span></span>  
 <span data-ttu-id="4d47d-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d47d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d47d-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4d47d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d47d-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4d47d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d47d-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d47d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
