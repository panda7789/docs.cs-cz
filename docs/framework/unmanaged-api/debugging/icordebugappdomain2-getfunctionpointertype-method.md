---
title: ICorDebugAppDomain2::GetFunctionPointerType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetFunctionPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType
helpviewer_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType method [.NET Framework debugging]
- GetFunctionPointerType method [.NET Framework debugging]
ms.assetid: 0aba6096-5b38-435c-a72a-86d35db4daef
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec1a9968dbec10783c6f1383fb523e95ff79561e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489745"
---
# <a name="icordebugappdomain2getfunctionpointertype-method"></a><span data-ttu-id="3b4a9-102">ICorDebugAppDomain2::GetFunctionPointerType – metoda</span><span class="sxs-lookup"><span data-stu-id="3b4a9-102">ICorDebugAppDomain2::GetFunctionPointerType Method</span></span>
<span data-ttu-id="3b4a9-103">Získá ukazatel na funkci, která má daným podpisem.</span><span class="sxs-lookup"><span data-stu-id="3b4a9-103">Gets a pointer to a function that has a given signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b4a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b4a9-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionPointerType (  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType   *ppTypeArgs[],  
    [out] ICorDebugType                      **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b4a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3b4a9-105">Parameters</span></span>  
 `nTypeArgs`  
 <span data-ttu-id="3b4a9-106">[in] Počet argumentů typu pro funkci.</span><span class="sxs-lookup"><span data-stu-id="3b4a9-106">[in] The number of type arguments for the function.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="3b4a9-107">[in] Pole ukazatelů, každý z nich odkazuje na objekt ICorDebugType, který představuje argument typu funkce.</span><span class="sxs-lookup"><span data-stu-id="3b4a9-107">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument of the function.</span></span> <span data-ttu-id="3b4a9-108">Prvním prvkem je návratový typ; Každý z dalších prvků je typ parametru.</span><span class="sxs-lookup"><span data-stu-id="3b4a9-108">The first element is the return type; each of the other elements is a parameter type.</span></span>  
  
 `ppType`  
 <span data-ttu-id="3b4a9-109">[out] Ukazatel na adresu `ICorDebugType` objekt, který představuje ukazatel na funkci.</span><span class="sxs-lookup"><span data-stu-id="3b4a9-109">[out] A pointer to the address of an `ICorDebugType` object that represents the pointer to the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b4a9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3b4a9-110">Requirements</span></span>  
 <span data-ttu-id="3b4a9-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b4a9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b4a9-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b4a9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b4a9-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b4a9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b4a9-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b4a9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
