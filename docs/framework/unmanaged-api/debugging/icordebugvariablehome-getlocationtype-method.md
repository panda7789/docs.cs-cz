---
title: ICorDebugVariableHome::GetLocationType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af879cbbf8edfd05e79d9b77b0c1fb71b2c835c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993652"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="ff1fb-102">ICorDebugVariableHome::GetLocationType – metoda</span><span class="sxs-lookup"><span data-stu-id="ff1fb-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="ff1fb-103">Získá typ proměnné nativní umístění.</span><span class="sxs-lookup"><span data-stu-id="ff1fb-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff1fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff1fb-104">Syntax</span></span>  
  
```  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff1fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff1fb-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="ff1fb-106">[out] Ukazatel na typ proměnné nativní umístění.</span><span class="sxs-lookup"><span data-stu-id="ff1fb-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="ff1fb-107">Zobrazit [variablelocationtype –](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) výčtu pro další informace.</span><span class="sxs-lookup"><span data-stu-id="ff1fb-107">See the [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff1fb-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff1fb-108">Requirements</span></span>  
 <span data-ttu-id="ff1fb-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff1fb-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff1fb-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff1fb-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff1fb-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff1fb-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff1fb-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff1fb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff1fb-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff1fb-113">See also</span></span>

- [<span data-ttu-id="ff1fb-114">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff1fb-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="ff1fb-115">VariableLocationType – výčet</span><span class="sxs-lookup"><span data-stu-id="ff1fb-115">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
