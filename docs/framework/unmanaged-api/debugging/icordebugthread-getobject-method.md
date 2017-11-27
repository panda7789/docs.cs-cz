---
title: "ICorDebugThread::GetObject – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetObject
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetObject method [.NET Framework debugging]
ms.assetid: 1590febe-96c2-4046-97db-d81d81d67e01
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 94e6d69ff2a873f387da0e93bcd859d53103d4b5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="3e392-102">ICorDebugThread::GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="3e392-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="3e392-103">Získá ukazatele rozhraní pro běžné vlákno language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="3e392-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e392-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e392-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3e392-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e392-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="3e392-106">[out] Ukazatel na adresu ICorDebugValue rozhraní objekt, který reprezentuje vlákno CLR.</span><span class="sxs-lookup"><span data-stu-id="3e392-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e392-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e392-107">Requirements</span></span>  
 <span data-ttu-id="3e392-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e392-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e392-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e392-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e392-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e392-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e392-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e392-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e392-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e392-112">See Also</span></span>  
 <xref:System.Threading.Thread>
