---
title: ICorDebugFrame::GetCallee – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a179b68e2196eeadc712ae8f7d023b2943533335
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995849"
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="3d787-102">ICorDebugFrame::GetCallee – metoda</span><span class="sxs-lookup"><span data-stu-id="3d787-102">ICorDebugFrame::GetCallee Method</span></span>
<span data-ttu-id="3d787-103">Získá ukazatel na objekt ICorDebugFrame v aktuální řetězec, který volá tento rámec.</span><span class="sxs-lookup"><span data-stu-id="3d787-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d787-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d787-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d787-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3d787-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="3d787-106">[out] Ukazatel na adresu `ICorDebugFrame` objekt, který reprezentuje volané rámce.</span><span class="sxs-lookup"><span data-stu-id="3d787-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="3d787-107">Tato hodnota je null, pokud volající snímek je vnitřní snímek aktuální řetězce.</span><span class="sxs-lookup"><span data-stu-id="3d787-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d787-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3d787-108">Requirements</span></span>  
 <span data-ttu-id="3d787-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d787-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d787-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d787-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d787-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d787-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d787-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d787-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
