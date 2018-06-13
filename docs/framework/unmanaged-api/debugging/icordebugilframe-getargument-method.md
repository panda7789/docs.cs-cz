---
title: ICorDebugILFrame::GetArgument – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1653913ca7410728f0f90a546f613a9d8b88be7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414050"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="9338c-102">ICorDebugILFrame::GetArgument – metoda</span><span class="sxs-lookup"><span data-stu-id="9338c-102">ICorDebugILFrame::GetArgument Method</span></span>
<span data-ttu-id="9338c-103">Získá hodnotu zadaného argumentu v této rámce zásobníku (MSIL intermediate language) společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9338c-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9338c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9338c-104">Syntax</span></span>  
  
```  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9338c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9338c-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="9338c-106">[v] Index v rámci této MSIL zásobníku argumentu.</span><span class="sxs-lookup"><span data-stu-id="9338c-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="9338c-107">[out] Ukazatel na adresu ICorDebugValue objekt, který reprezentuje načtené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9338c-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9338c-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9338c-108">Remarks</span></span>  
 <span data-ttu-id="9338c-109">`GetArgument` Metodu lze použít rámce zásobníku MSIL nebo v rámci kompilované v běhu (JIT).</span><span class="sxs-lookup"><span data-stu-id="9338c-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9338c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9338c-110">Requirements</span></span>  
 <span data-ttu-id="9338c-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9338c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9338c-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9338c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9338c-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9338c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9338c-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9338c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
