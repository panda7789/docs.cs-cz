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
ms.openlocfilehash: 4fced656168952c1064de213405147baf7856b2c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737356"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="df341-102">ICorDebugAssembly::GetAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="df341-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="df341-103">Získá ukazatel rozhraní k doméně aplikace, která obsahuje tato `ICorDebugAssembly` instance.</span><span class="sxs-lookup"><span data-stu-id="df341-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df341-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df341-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df341-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="df341-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="df341-106">[out] Ukazatel na adresu icordebugappdomain – rozhraní, která představuje doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="df341-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df341-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="df341-107">Remarks</span></span>  
 <span data-ttu-id="df341-108">Pokud toto sestavení je sestavení systému `GetAppDomain` , vrátí hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="df341-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df341-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="df341-109">Requirements</span></span>  
 <span data-ttu-id="df341-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df341-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df341-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df341-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df341-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df341-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df341-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df341-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
