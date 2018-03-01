---
title: "ICorDebugEval2::NewStringWithLength – metoda"
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
- ICorDebugEval2.NewStringWithLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1cd2bc201210bc9af8c13c83553b581c080f658a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="14942-102">ICorDebugEval2::NewStringWithLength – metoda</span><span class="sxs-lookup"><span data-stu-id="14942-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="14942-103">Vytvoří řetězec na určenou délku zadaný obsah.</span><span class="sxs-lookup"><span data-stu-id="14942-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14942-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14942-104">Syntax</span></span>  
  
```  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="14942-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14942-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="14942-106">[v] Ukazatel na hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="14942-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="14942-107">[v] Délka řetězce.</span><span class="sxs-lookup"><span data-stu-id="14942-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14942-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14942-108">Remarks</span></span>  
 <span data-ttu-id="14942-109">Pokud je řetězec koncové znak hodnoty null musí být ve spravovaných řetězci volající `NewStringWithLength` metoda Ujistěte se, že obsahuje délku řetězce znakem null.</span><span class="sxs-lookup"><span data-stu-id="14942-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="14942-110">Řetězec se vždy vytvoří v doméně aplikace, ve kterém je aktuálně spuštěných vlákno.</span><span class="sxs-lookup"><span data-stu-id="14942-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14942-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14942-111">Requirements</span></span>  
 <span data-ttu-id="14942-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14942-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14942-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14942-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14942-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14942-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14942-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14942-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
