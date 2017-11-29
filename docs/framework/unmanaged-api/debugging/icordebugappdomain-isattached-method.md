---
title: "ICorDebugAppDomain::IsAttached – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.IsAttached
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a85b674ad705f77e00cf2a8a5286d6a74f7a646
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="fc707-102">ICorDebugAppDomain::IsAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="fc707-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="fc707-103">Získá hodnotu, která určuje, zda je ladicí program připojen do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="fc707-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc707-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc707-104">Syntax</span></span>  
  
```  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc707-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc707-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="fc707-106">[out] `true` Pokud ladicího programu je připojené k doméně aplikace, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="fc707-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc707-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc707-107">Remarks</span></span>  
 <span data-ttu-id="fc707-108">ICorDebugController metody nemohou používat, dokud ladicí program připojí k doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="fc707-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc707-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc707-109">Requirements</span></span>  
 <span data-ttu-id="fc707-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc707-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc707-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc707-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc707-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc707-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc707-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc707-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
