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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49f5ed8b24d81ba8f32a9fe0ad7488693718bde9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468556"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="d4cab-102">ICorDebugArrayValue::HasBaseIndicies – metoda</span><span class="sxs-lookup"><span data-stu-id="d4cab-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="d4cab-103">Získá hodnotu, která určuje, zda dimenzí tohoto pole mají základní index nenulové.</span><span class="sxs-lookup"><span data-stu-id="d4cab-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4cab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4cab-104">Syntax</span></span>  
  
```  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4cab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4cab-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="d4cab-106">[out] Ukazatel na logickou hodnotu, která je `true` Pokud jeden nebo více dimenzí tohoto `ICorDebugArrayValue` objekt mít základní index nenulové; v opačném případě je logická hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="d4cab-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4cab-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4cab-107">Requirements</span></span>  
 <span data-ttu-id="d4cab-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4cab-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4cab-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4cab-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4cab-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4cab-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4cab-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4cab-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
