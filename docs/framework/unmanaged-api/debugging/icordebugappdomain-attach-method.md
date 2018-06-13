---
title: ICorDebugAppDomain::Attach – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.Attach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::Attach
helpviewer_keywords:
- ICorDebugAppDomain::Attach method [.NET Framework debugging]
- Attach method [.NET Framework debugging]
ms.assetid: 0358b84a-4236-4c34-945b-4babff7df570
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a290ca162e5ab71b4184d166bcd00f1d0217cb94
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402493"
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="5f75a-102">ICorDebugAppDomain::Attach – metoda</span><span class="sxs-lookup"><span data-stu-id="5f75a-102">ICorDebugAppDomain::Attach Method</span></span>
<span data-ttu-id="5f75a-103">Připojí ladicí program do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="5f75a-103">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f75a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f75a-104">Syntax</span></span>  
  
```  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5f75a-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5f75a-105">Remarks</span></span>  
 <span data-ttu-id="5f75a-106">Ladicí program musí být připojené k doméně aplikace pro příjem událostí a chcete povolit ladění domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="5f75a-106">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f75a-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5f75a-107">Requirements</span></span>  
 <span data-ttu-id="5f75a-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f75a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f75a-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f75a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f75a-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f75a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f75a-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f75a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
