---
title: ICorDebugFrame::GetCode – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCode
helpviewer_keywords:
- GetCode method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCode method [.NET Framework debugging]
ms.assetid: fbaa0794-a031-4015-8beb-2749e47ac340
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7a4e8c6fa91ee43c33fe0f99d50bd4b1af4a0fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988777"
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="5d556-102">ICorDebugFrame::GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="5d556-102">ICorDebugFrame::GetCode Method</span></span>
<span data-ttu-id="5d556-103">Získá ukazatel na kód spojený s rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="5d556-103">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d556-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d556-104">Syntax</span></span>  
  
```  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d556-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d556-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="5d556-106">[out] Ukazatel na adresu ICorDebugCode objekt, který představuje kód spojený s tohoto rámce.</span><span class="sxs-lookup"><span data-stu-id="5d556-106">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d556-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d556-107">Requirements</span></span>  
 <span data-ttu-id="5d556-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d556-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d556-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d556-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d556-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d556-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d556-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d556-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
