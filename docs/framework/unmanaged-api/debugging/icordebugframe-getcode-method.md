---
title: "ICorDebugFrame::GetCode – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.GetCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::GetCode
helpviewer_keywords:
- GetCode method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCode method [.NET Framework debugging]
ms.assetid: fbaa0794-a031-4015-8beb-2749e47ac340
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a99b652a439a284033f3e7a9ecc46b3599fae00b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="22e7a-102">ICorDebugFrame::GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="22e7a-102">ICorDebugFrame::GetCode Method</span></span>
<span data-ttu-id="22e7a-103">Získá ukazatel kódu přidružené k této rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="22e7a-103">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22e7a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22e7a-104">Syntax</span></span>  
  
```  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="22e7a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22e7a-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="22e7a-106">[out] Ukazatel na adresu ICorDebugCode objekt, který představuje kód spojený s tohoto snímku.</span><span class="sxs-lookup"><span data-stu-id="22e7a-106">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22e7a-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22e7a-107">Requirements</span></span>  
 <span data-ttu-id="22e7a-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22e7a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22e7a-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="22e7a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22e7a-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22e7a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22e7a-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22e7a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
