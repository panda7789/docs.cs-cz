---
title: "ICorDebugInternalFrame::GetFrameType – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame.GetFrameType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 476903ae8f1461a46d685bc3e549c3b6553d5c68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="2f907-102">ICorDebugInternalFrame::GetFrameType – metoda</span><span class="sxs-lookup"><span data-stu-id="2f907-102">ICorDebugInternalFrame::GetFrameType Method</span></span>
<span data-ttu-id="2f907-103">Získá typ této interní rámce.</span><span class="sxs-lookup"><span data-stu-id="2f907-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f907-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f907-104">Syntax</span></span>  
  
```  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2f907-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f907-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="2f907-106">[out] Ukazatel na hodnotu CorDebugInternalFrameType – výčet, který určuje typ interní rámce reprezentována to `ICorDebugInternalFrame` objektu.</span><span class="sxs-lookup"><span data-stu-id="2f907-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f907-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f907-107">Remarks</span></span>  
 <span data-ttu-id="2f907-108">Typ interní rámce nebude nikdy STUBFRAME_NONE.</span><span class="sxs-lookup"><span data-stu-id="2f907-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="2f907-109">Ladicí programy by měly řádně ignorovat nerozpoznané interní rámce typy.</span><span class="sxs-lookup"><span data-stu-id="2f907-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f907-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f907-110">Requirements</span></span>  
 <span data-ttu-id="2f907-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f907-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f907-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f907-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f907-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f907-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f907-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f907-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
