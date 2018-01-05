---
title: "ICorDebugAppDomain::GetObject – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.GetObject
api_location: corguids.lib
api_type: COM
f1_keywords: ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f8206c6e5efbee8522f425f9078d99a39bbdd42
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="10ae2-102">ICorDebugAppDomain::GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="10ae2-102">ICorDebugAppDomain::GetObject Method</span></span>
<span data-ttu-id="10ae2-103">Získá ukazatele rozhraní pro běžné domény aplikace language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="10ae2-103">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10ae2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10ae2-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10ae2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="10ae2-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="10ae2-106">[out] Ukazatel na adresu ICorDebugValue rozhraní objekt, který reprezentuje doméně CLR aplikace.</span><span class="sxs-lookup"><span data-stu-id="10ae2-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10ae2-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="10ae2-107">Return Value</span></span>  
 <span data-ttu-id="10ae2-108">Pokud spravované <xref:System.AppDomain?displayProperty=nameWithType> objekt nebyl byl vytvořen pro tuto doménu aplikace, vrátí metoda `S_FALSE` a umístí `NULL` v `*ppObject`.</span><span class="sxs-lookup"><span data-stu-id="10ae2-108">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10ae2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="10ae2-109">Remarks</span></span>  
 <span data-ttu-id="10ae2-110">Každou doménu aplikace v procesu může mít spravované <xref:System.AppDomain?displayProperty=nameWithType> objektu v modulu runtime, který ho zastupuje.</span><span class="sxs-lookup"><span data-stu-id="10ae2-110">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="10ae2-111">Tato funkce získá ICorDebugValue rozhraní objekt, který odpovídá tomuto spravované <xref:System.AppDomain?displayProperty=nameWithType> objektu.</span><span class="sxs-lookup"><span data-stu-id="10ae2-111">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10ae2-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="10ae2-112">Requirements</span></span>  
 <span data-ttu-id="10ae2-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10ae2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10ae2-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10ae2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10ae2-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10ae2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10ae2-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10ae2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
