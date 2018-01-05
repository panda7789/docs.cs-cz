---
title: "ICorDebugAppDomain::Attach – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.Attach
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::Attach
helpviewer_keywords:
- ICorDebugAppDomain::Attach method [.NET Framework debugging]
- Attach method [.NET Framework debugging]
ms.assetid: 0358b84a-4236-4c34-945b-4babff7df570
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ba725cfe4aabab14de4b64297a038bf0b0ccec0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="67db1-102">ICorDebugAppDomain::Attach – metoda</span><span class="sxs-lookup"><span data-stu-id="67db1-102">ICorDebugAppDomain::Attach Method</span></span>
<span data-ttu-id="67db1-103">Připojí ladicí program do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="67db1-103">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67db1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67db1-104">Syntax</span></span>  
  
```  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="67db1-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="67db1-105">Remarks</span></span>  
 <span data-ttu-id="67db1-106">Ladicí program musí být připojené k doméně aplikace pro příjem událostí a chcete povolit ladění domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="67db1-106">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67db1-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="67db1-107">Requirements</span></span>  
 <span data-ttu-id="67db1-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67db1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67db1-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67db1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67db1-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67db1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67db1-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67db1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
