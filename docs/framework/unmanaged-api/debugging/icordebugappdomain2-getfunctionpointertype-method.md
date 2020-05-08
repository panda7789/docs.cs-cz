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
ms.openlocfilehash: fb9b5ee329b41a8b842b94d59bd61c8bcf5f0bf5
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895150"
---
# <a name="icordebugappdomain2getfunctionpointertype-method"></a><span data-ttu-id="73d38-102">ICorDebugAppDomain2::GetFunctionPointerType – metoda</span><span class="sxs-lookup"><span data-stu-id="73d38-102">ICorDebugAppDomain2::GetFunctionPointerType Method</span></span>
<span data-ttu-id="73d38-103">Získá ukazatel na funkci, která má daný podpis.</span><span class="sxs-lookup"><span data-stu-id="73d38-103">Gets a pointer to a function that has a given signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73d38-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73d38-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionPointerType (  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType   *ppTypeArgs[],  
    [out] ICorDebugType                      **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73d38-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73d38-105">Parameters</span></span>  
 `nTypeArgs`  
 <span data-ttu-id="73d38-106">pro Počet argumentů typu pro funkci</span><span class="sxs-lookup"><span data-stu-id="73d38-106">[in] The number of type arguments for the function.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="73d38-107">pro Pole ukazatelů, z nichž každý odkazuje na objekt ICorDebugType, který představuje argument typu funkce.</span><span class="sxs-lookup"><span data-stu-id="73d38-107">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument of the function.</span></span> <span data-ttu-id="73d38-108">První prvek je návratový typ; Každý z ostatních prvků je typ parametru.</span><span class="sxs-lookup"><span data-stu-id="73d38-108">The first element is the return type; each of the other elements is a parameter type.</span></span>  
  
 `ppType`  
 <span data-ttu-id="73d38-109">mimo Ukazatel na adresu `ICorDebugType` objektu, který představuje ukazatel na funkci.</span><span class="sxs-lookup"><span data-stu-id="73d38-109">[out] A pointer to the address of an `ICorDebugType` object that represents the pointer to the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73d38-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73d38-110">Requirements</span></span>  
 <span data-ttu-id="73d38-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73d38-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73d38-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="73d38-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73d38-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="73d38-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73d38-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73d38-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
