---
title: ICorDebugArrayValue::GetDimensions – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetDimensions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetDimensions
helpviewer_keywords:
- ICorDebugArrayValue::GetDimensions method [.NET Framework debugging]
- GetDimensions method [.NET Framework debugging]
ms.assetid: 6c116592-134b-4ef2-a319-680e92d013aa
topic_type:
- apiref
ms.openlocfilehash: c5199794098e4d83588728eeb165aee5f81fe4c4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088502"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a><span data-ttu-id="e0d6e-102">ICorDebugArrayValue::GetDimensions – metoda</span><span class="sxs-lookup"><span data-stu-id="e0d6e-102">ICorDebugArrayValue::GetDimensions Method</span></span>
<span data-ttu-id="e0d6e-103">Získá počet prvků v každé dimenzi tohoto pole.</span><span class="sxs-lookup"><span data-stu-id="e0d6e-103">Gets the number of elements in each dimension of this array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0d6e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0d6e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0d6e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0d6e-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="e0d6e-106">pro Počet dimenzí tohoto objektu ICorDebugArrayValue</span><span class="sxs-lookup"><span data-stu-id="e0d6e-106">[in] The number of dimensions of this ICorDebugArrayValue object.</span></span>  
  
 <span data-ttu-id="e0d6e-107">Tato hodnota je také velikost pole `dims`, protože jeho velikost je rovna počtu rozměrů `ICorDebugArrayValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="e0d6e-107">This value is also the size of the `dims` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `dims`  
 <span data-ttu-id="e0d6e-108">mimo Pole celých čísel, z nichž každý Určuje počet prvků v dimenzi v tomto objektu `ICorDebugArrayValue`.</span><span class="sxs-lookup"><span data-stu-id="e0d6e-108">[out] An array of integers, each of which specifies the number of elements in a dimension in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0d6e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0d6e-109">Requirements</span></span>  
 <span data-ttu-id="e0d6e-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0d6e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0d6e-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e0d6e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0d6e-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e0d6e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0d6e-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0d6e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
