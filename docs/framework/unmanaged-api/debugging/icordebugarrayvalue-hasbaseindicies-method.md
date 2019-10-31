---
title: ICorDebugArrayValue::HasBaseIndicies – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.HasBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::HasBaseIndicies
helpviewer_keywords:
- HasBaseIndicies method [.NET Framework debugging]
- ICorDebugArrayValue::HasBaseIndicies method [.NET Framework debugging]
ms.assetid: aa26df07-e0a6-4608-bdef-d4afafec89aa
topic_type:
- apiref
ms.openlocfilehash: 418ebb51df3f2d86011ee2e77022c3ee5c7ac0b0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088233"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="2c0b6-102">ICorDebugArrayValue::HasBaseIndicies – metoda</span><span class="sxs-lookup"><span data-stu-id="2c0b6-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="2c0b6-103">Získá hodnotu, která označuje, zda jakékoli dimenze v tomto poli mají základní index nenulového typu.</span><span class="sxs-lookup"><span data-stu-id="2c0b6-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c0b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c0b6-104">Syntax</span></span>  
  
```cpp  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c0b6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c0b6-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="2c0b6-106">mimo Ukazatel na logickou hodnotu, která je `true`, pokud jedna nebo více dimenzí tohoto objektu `ICorDebugArrayValue` mají základní index nenulového typu; v opačném případě je logická hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="2c0b6-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c0b6-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2c0b6-107">Requirements</span></span>  
 <span data-ttu-id="2c0b6-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c0b6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c0b6-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2c0b6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c0b6-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2c0b6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c0b6-111">**Verze .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c0b6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
