---
title: "CreateApplicationContext – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CreateApplicationContext
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateApplicationContext
helpviewer_keywords:
- CreateApplicationContext function [.NET Framework fusion]
ms.assetid: 7bf8a141-b2c0-4058-9885-1cef7dcaa811
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 89c3181a157ce5162d93d1df14641b393fb3082d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="893c1-102">CreateApplicationContext – funkce</span><span class="sxs-lookup"><span data-stu-id="893c1-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="893c1-103">Tato funkce podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="893c1-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="893c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="893c1-104">Syntax</span></span>  
  
```  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="893c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="893c1-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="893c1-106">[v] Ukazatel na popisný název.</span><span class="sxs-lookup"><span data-stu-id="893c1-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="893c1-107">[out] Ukazatel na kontext aplikace.</span><span class="sxs-lookup"><span data-stu-id="893c1-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="893c1-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="893c1-108">Requirements</span></span>  
 <span data-ttu-id="893c1-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="893c1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="893c1-110">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="893c1-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="893c1-111">**Knihovna:** zahrnuty jako prostředek v knihovně Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="893c1-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="893c1-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="893c1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="893c1-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="893c1-113">See Also</span></span>  
 [<span data-ttu-id="893c1-114">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="893c1-114">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [<span data-ttu-id="893c1-115">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="893c1-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [<span data-ttu-id="893c1-116">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="893c1-116">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
