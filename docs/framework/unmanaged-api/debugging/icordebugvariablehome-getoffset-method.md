---
title: "ICorDebugVariableHome::GetOffset – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetOffset
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09f80a362d4b44d13c39218b9d7a0db11ef49f78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="b5f81-102">ICorDebugVariableHome::GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="b5f81-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="b5f81-103">Získá posun od základní registrace proměnné.</span><span class="sxs-lookup"><span data-stu-id="b5f81-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5f81-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5f81-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5f81-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5f81-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="b5f81-106">[out] Posun od základní registrace.</span><span class="sxs-lookup"><span data-stu-id="b5f81-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5f81-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b5f81-107">Return Value</span></span>  
 <span data-ttu-id="b5f81-108">Metoda vrátí následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="b5f81-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="b5f81-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b5f81-109">Value</span></span>|<span data-ttu-id="b5f81-110">Popis</span><span class="sxs-lookup"><span data-stu-id="b5f81-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="b5f81-111">Proměnná je v paměti register relativní umístění.</span><span class="sxs-lookup"><span data-stu-id="b5f81-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="b5f81-112">Proměnná se nenachází v paměti register relativní umístění.</span><span class="sxs-lookup"><span data-stu-id="b5f81-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b5f81-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5f81-113">Requirements</span></span>  
 <span data-ttu-id="b5f81-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5f81-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5f81-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b5f81-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5f81-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5f81-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5f81-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5f81-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5f81-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5f81-118">See Also</span></span>  
 [<span data-ttu-id="b5f81-119">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b5f81-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
