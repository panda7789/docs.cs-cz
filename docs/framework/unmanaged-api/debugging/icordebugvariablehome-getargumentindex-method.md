---
title: "ICorDebugVariableHome::GetArgumentIndex – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetArgumentIndex
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentiIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 175e45758d26d8168279c825d41ee58d049edf0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="69cc3-102">ICorDebugVariableHome::GetArgumentIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="69cc3-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>
<span data-ttu-id="69cc3-103">Získá index argument funkce.</span><span class="sxs-lookup"><span data-stu-id="69cc3-103">Gets the index of a function argument.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69cc3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69cc3-104">Syntax</span></span>  
  
```  
HRESULT GetArgumentIndex(  
    [out] ULONG32* pArgumentIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69cc3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69cc3-105">Parameters</span></span>  
 `pArgumentIndex`  
 <span data-ttu-id="69cc3-106">[out] Ukazatel na argument index.</span><span class="sxs-lookup"><span data-stu-id="69cc3-106">[out] A pointer to the argument index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69cc3-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="69cc3-107">Return Value</span></span>  
 <span data-ttu-id="69cc3-108">Metoda vrátí následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="69cc3-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="69cc3-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="69cc3-109">Value</span></span>|<span data-ttu-id="69cc3-110">Popis</span><span class="sxs-lookup"><span data-stu-id="69cc3-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="69cc3-111">Volání metody, které vrátil platný argument indexu.</span><span class="sxs-lookup"><span data-stu-id="69cc3-111">The method call returned a valid argument index.</span></span>|  
|`E_FAIL`|<span data-ttu-id="69cc3-112">Aktuální [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance představuje místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="69cc3-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69cc3-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="69cc3-113">Remarks</span></span>  
 <span data-ttu-id="69cc3-114">Argument indexu lze načíst metadata pro tento argument.</span><span class="sxs-lookup"><span data-stu-id="69cc3-114">The argument index can be used to retrieve metadata for this argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69cc3-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="69cc3-115">Requirements</span></span>  
 <span data-ttu-id="69cc3-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69cc3-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69cc3-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69cc3-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69cc3-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69cc3-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69cc3-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69cc3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69cc3-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="69cc3-120">See Also</span></span>  
 [<span data-ttu-id="69cc3-121">ICorDebugVariableHome rozhraní</span><span class="sxs-lookup"><span data-stu-id="69cc3-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
