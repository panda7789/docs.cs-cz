---
title: ICorDebugAssembly::GetAppDomain – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetAppDomain
helpviewer_keywords:
- ICorDebugAssembly::GetAppDomain method [.NET Framework debugging]
- GetAppDomain method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 14e18510-23ac-4cba-9f96-c86147a2df9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e22d112d1414b13033f73723821e5e4b5764e1c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401976"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="6fdf7-102">ICorDebugAssembly::GetAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="6fdf7-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="6fdf7-103">Získá ukazatele rozhraní k doméně aplikace, která obsahuje toto `ICorDebugAssembly` instance.</span><span class="sxs-lookup"><span data-stu-id="6fdf7-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fdf7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fdf7-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6fdf7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6fdf7-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="6fdf7-106">[out] Ukazatel na adresu ICorDebugAppDomain rozhraní, které představuje doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="6fdf7-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fdf7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6fdf7-107">Remarks</span></span>  
 <span data-ttu-id="6fdf7-108">Pokud je toto sestavení sestavení systému `GetAppDomain` , vrátí hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="6fdf7-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fdf7-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6fdf7-109">Requirements</span></span>  
 <span data-ttu-id="6fdf7-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fdf7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fdf7-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6fdf7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fdf7-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fdf7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fdf7-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fdf7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
