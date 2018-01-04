---
title: "ICorDebugAssembly::GetAppDomain – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly.GetAppDomain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly::GetAppDomain
helpviewer_keywords:
- ICorDebugAssembly::GetAppDomain method [.NET Framework debugging]
- GetAppDomain method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 14e18510-23ac-4cba-9f96-c86147a2df9d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f97795568b9811d0dbf7852fd64d5256c29b8f30
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="8b1c1-102">ICorDebugAssembly::GetAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="8b1c1-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="8b1c1-103">Získá ukazatele rozhraní k doméně aplikace, která obsahuje toto `ICorDebugAssembly` instance.</span><span class="sxs-lookup"><span data-stu-id="8b1c1-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b1c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b1c1-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b1c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b1c1-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="8b1c1-106">[out] Ukazatel na adresu ICorDebugAppDomain rozhraní, které představuje doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="8b1c1-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b1c1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b1c1-107">Remarks</span></span>  
 <span data-ttu-id="8b1c1-108">Pokud je toto sestavení sestavení systému `GetAppDomain` , vrátí hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="8b1c1-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b1c1-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b1c1-109">Requirements</span></span>  
 <span data-ttu-id="8b1c1-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b1c1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b1c1-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b1c1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b1c1-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b1c1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b1c1-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b1c1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
