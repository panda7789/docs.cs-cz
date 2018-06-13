---
title: ICorDebugFrame::GetCaller – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCaller
helpviewer_keywords:
- GetCaller method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCaller method [.NET Framework debugging]
ms.assetid: bfdc946b-8238-4eb9-8a85-884049fb0fd4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2452f4be0acde300676bf56011416e0a9ef16464
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411713"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="fb087-102">ICorDebugFrame::GetCaller – metoda</span><span class="sxs-lookup"><span data-stu-id="fb087-102">ICorDebugFrame::GetCaller Method</span></span>
<span data-ttu-id="fb087-103">Získá ukazatel na objekt ICorDebugFrame v aktuální řetězec, který volá tento snímek.</span><span class="sxs-lookup"><span data-stu-id="fb087-103">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb087-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb087-104">Syntax</span></span>  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb087-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb087-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="fb087-106">[out] Ukazatel na adresu `ICorDebugFrame` objekt, který reprezentuje volání rámečku.</span><span class="sxs-lookup"><span data-stu-id="fb087-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="fb087-107">Tato hodnota je null, pokud je názvem rámečku nejkrajnější rámečku v řetězu aktuální.</span><span class="sxs-lookup"><span data-stu-id="fb087-107">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb087-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb087-108">Requirements</span></span>  
 <span data-ttu-id="fb087-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb087-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb087-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb087-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb087-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb087-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb087-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb087-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
