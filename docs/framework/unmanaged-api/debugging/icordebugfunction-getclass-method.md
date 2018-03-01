---
title: "ICorDebugFunction::GetClass – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugFunction.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetClass
helpviewer_keywords:
- GetClass method, ICorDebugFunction interface [.NET Framework debugging]
- ICorDebugFunction::GetClass method [.NET Framework debugging]
ms.assetid: 27967230-144f-40d3-9e23-961d0241abd9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4607b5c71311eeccc9df778a45ca30a305b90aa9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="70389-102">ICorDebugFunction::GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="70389-102">ICorDebugFunction::GetClass Method</span></span>
<span data-ttu-id="70389-103">Získá objekt ICorDebugClass, který představuje třídu, ke které tato funkce je členem skupiny.</span><span class="sxs-lookup"><span data-stu-id="70389-103">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70389-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70389-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70389-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70389-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="70389-106">[out] Ukazatel na adresu `ICorDebugClass` objekt, který reprezentuje třídu, nebo hodnotu null, pokud je tato funkce není členem třídy.</span><span class="sxs-lookup"><span data-stu-id="70389-106">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70389-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70389-107">Requirements</span></span>  
 <span data-ttu-id="70389-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70389-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70389-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70389-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70389-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70389-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70389-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70389-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
