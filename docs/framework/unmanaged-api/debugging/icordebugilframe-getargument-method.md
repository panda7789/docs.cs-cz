---
title: "ICorDebugILFrame::GetArgument – metoda"
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
- ICorDebugILFrame.GetArgument
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c6b1c097d830af4e68035f79670983002c15c16d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="4750b-102">ICorDebugILFrame::GetArgument – metoda</span><span class="sxs-lookup"><span data-stu-id="4750b-102">ICorDebugILFrame::GetArgument Method</span></span>
<span data-ttu-id="4750b-103">Získá hodnotu zadaného argumentu v této rámce zásobníku (MSIL intermediate language) společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4750b-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4750b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4750b-104">Syntax</span></span>  
  
```  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4750b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4750b-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="4750b-106">[v] Index v rámci této MSIL zásobníku argumentu.</span><span class="sxs-lookup"><span data-stu-id="4750b-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="4750b-107">[out] Ukazatel na adresu ICorDebugValue objekt, který reprezentuje načtené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4750b-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4750b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4750b-108">Remarks</span></span>  
 <span data-ttu-id="4750b-109">`GetArgument` Metodu lze použít rámce zásobníku MSIL nebo v rámci kompilované v běhu (JIT).</span><span class="sxs-lookup"><span data-stu-id="4750b-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4750b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4750b-110">Requirements</span></span>  
 <span data-ttu-id="4750b-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4750b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4750b-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4750b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4750b-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4750b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4750b-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4750b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
