---
title: ICorDebugFunction::GetModule – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetModule
helpviewer_keywords:
- ICorDebugFunction::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 5031a5d3-2564-412a-9007-e36d4631308a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aef12634da477e72757e98e520b600ec1ee0f1b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412162"
---
# <a name="icordebugfunctiongetmodule-method"></a><span data-ttu-id="085e4-102">ICorDebugFunction::GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="085e4-102">ICorDebugFunction::GetModule Method</span></span>
<span data-ttu-id="085e4-103">Získá modul, ve kterém je definována funkce.</span><span class="sxs-lookup"><span data-stu-id="085e4-103">Gets the module in which this function is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="085e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="085e4-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="085e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="085e4-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="085e4-106">[out] Ukazatel na adresu ICorDebugModule objekt, který představuje modul, ve kterém je definována funkce.</span><span class="sxs-lookup"><span data-stu-id="085e4-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this function is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="085e4-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="085e4-107">Requirements</span></span>  
 <span data-ttu-id="085e4-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="085e4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="085e4-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="085e4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="085e4-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="085e4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="085e4-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="085e4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
