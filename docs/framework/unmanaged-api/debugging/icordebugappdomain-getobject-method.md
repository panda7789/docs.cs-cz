---
title: ICorDebugAppDomain::GetObject – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetObject
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6f528bcef7d06b503b1ee9d7bd4a61d3d3e9672
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406517"
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="7513b-102">ICorDebugAppDomain::GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="7513b-102">ICorDebugAppDomain::GetObject Method</span></span>
<span data-ttu-id="7513b-103">Získá ukazatele rozhraní pro běžné domény aplikace language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="7513b-103">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7513b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7513b-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7513b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7513b-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="7513b-106">[out] Ukazatel na adresu ICorDebugValue rozhraní objekt, který reprezentuje doméně CLR aplikace.</span><span class="sxs-lookup"><span data-stu-id="7513b-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7513b-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7513b-107">Return Value</span></span>  
 <span data-ttu-id="7513b-108">Pokud spravované <xref:System.AppDomain?displayProperty=nameWithType> objekt nebyl byl vytvořen pro tuto doménu aplikace, vrátí metoda `S_FALSE` a umístí `NULL` v `*ppObject`.</span><span class="sxs-lookup"><span data-stu-id="7513b-108">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7513b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7513b-109">Remarks</span></span>  
 <span data-ttu-id="7513b-110">Každou doménu aplikace v procesu může mít spravované <xref:System.AppDomain?displayProperty=nameWithType> objektu v modulu runtime, který ho zastupuje.</span><span class="sxs-lookup"><span data-stu-id="7513b-110">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="7513b-111">Tato funkce získá ICorDebugValue rozhraní objekt, který odpovídá tomuto spravované <xref:System.AppDomain?displayProperty=nameWithType> objektu.</span><span class="sxs-lookup"><span data-stu-id="7513b-111">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7513b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7513b-112">Requirements</span></span>  
 <span data-ttu-id="7513b-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7513b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7513b-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7513b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7513b-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7513b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7513b-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7513b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
