---
title: ICorDebugInternalFrame::GetFrameType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame.GetFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a0b6f0550bad534379b562c3df9da9ab917f5270
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946333"
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="a5ade-102">ICorDebugInternalFrame::GetFrameType – metoda</span><span class="sxs-lookup"><span data-stu-id="a5ade-102">ICorDebugInternalFrame::GetFrameType Method</span></span>
<span data-ttu-id="a5ade-103">Získá typ této vnitřní rámec.</span><span class="sxs-lookup"><span data-stu-id="a5ade-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5ade-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5ade-104">Syntax</span></span>  
  
```  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5ade-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5ade-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="a5ade-106">[out] Ukazatel na hodnotu cordebuginternalframetype – výčet, který označuje typ vnitřní rámec představovaného tímto rozhraním `ICorDebugInternalFrame` objektu.</span><span class="sxs-lookup"><span data-stu-id="a5ade-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5ade-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5ade-107">Remarks</span></span>  
 <span data-ttu-id="a5ade-108">Typ vnitřní rámec již nikdy nebude STUBFRAME_NONE.</span><span class="sxs-lookup"><span data-stu-id="a5ade-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="a5ade-109">Ladicí programy by měly řádně ignorovat nerozpoznaný snímek vnitřní typy.</span><span class="sxs-lookup"><span data-stu-id="a5ade-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5ade-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a5ade-110">Requirements</span></span>  
 <span data-ttu-id="a5ade-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5ade-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5ade-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5ade-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5ade-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5ade-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5ade-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5ade-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
