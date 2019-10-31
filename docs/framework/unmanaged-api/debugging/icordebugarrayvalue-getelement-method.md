---
title: ICorDebugArrayValue::GetElement – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
ms.openlocfilehash: 3d45caae56403d77776f1a8adbb5fb9c368ff105
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088495"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="f5cc5-102">ICorDebugArrayValue::GetElement – metoda</span><span class="sxs-lookup"><span data-stu-id="f5cc5-102">ICorDebugArrayValue::GetElement Method</span></span>
<span data-ttu-id="f5cc5-103">Získá hodnotu daného elementu pole.</span><span class="sxs-lookup"><span data-stu-id="f5cc5-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5cc5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5cc5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]   
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5cc5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5cc5-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="f5cc5-106">pro Počet dimenzí tohoto objektu `ICorDebugArrayValue`.</span><span class="sxs-lookup"><span data-stu-id="f5cc5-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="f5cc5-107">Tato hodnota je také velikost pole `indices`, protože jeho velikost je rovna počtu rozměrů `ICorDebugArrayValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="f5cc5-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="f5cc5-108">pro Pole hodnot indexu, z nichž každý Určuje pozici v rámci dimenze objektu `ICorDebugArrayValue`.</span><span class="sxs-lookup"><span data-stu-id="f5cc5-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="f5cc5-109">Tato hodnota nesmí být null.</span><span class="sxs-lookup"><span data-stu-id="f5cc5-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="f5cc5-110">mimo Ukazatel na adresu objektu ICorDebugValue, který představuje hodnotu zadaného elementu.</span><span class="sxs-lookup"><span data-stu-id="f5cc5-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5cc5-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5cc5-111">Requirements</span></span>  
 <span data-ttu-id="f5cc5-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5cc5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5cc5-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f5cc5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5cc5-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f5cc5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5cc5-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5cc5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
