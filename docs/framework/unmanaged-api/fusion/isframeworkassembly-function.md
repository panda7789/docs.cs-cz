---
title: IsFrameworkAssembly – funkce
ms.date: 03/30/2017
api_name:
- IsFrameworkAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IsFrameworkAssembly
helpviewer_keywords:
- IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e231c4fa51e6e66cba6227233cf73dd1cd4ebbe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733919"
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="1a70a-102">IsFrameworkAssembly – funkce</span><span class="sxs-lookup"><span data-stu-id="1a70a-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="1a70a-103">Získá hodnotu, která určuje, zda se spravuje zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="1a70a-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a70a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a70a-104">Syntax</span></span>  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1a70a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a70a-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="1a70a-106">[in] Název sestavení ke kontrole.</span><span class="sxs-lookup"><span data-stu-id="1a70a-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="1a70a-107">[out] Logická hodnota, která určuje, jestli je spravované sestavení.</span><span class="sxs-lookup"><span data-stu-id="1a70a-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="1a70a-108">[in] Uncanonicalized řetězec, který obsahuje jedinečné identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="1a70a-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="1a70a-109">[in] Velikost `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="1a70a-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a70a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1a70a-110">Remarks</span></span>  
 <span data-ttu-id="1a70a-111">`pwzAssemblyReference` Parametrem je ukazatel na řetězec znaků, který obsahuje název sestavení.</span><span class="sxs-lookup"><span data-stu-id="1a70a-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="1a70a-112">Pokud je toto sestavení součástí .NET Framework `pbIsFrameworkAssembly` parametr bude obsahovat hodnotu typu Boolean `true`.</span><span class="sxs-lookup"><span data-stu-id="1a70a-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="1a70a-113">Pokud pojmenované sestavení není součástí rozhraní .NET Framework, nebo pokud `pwzAssemblyReference` sestavení, nikoli název parametru `pbIsFrameworkAssembly` bude obsahovat hodnotu typu Boolean `false`.</span><span class="sxs-lookup"><span data-stu-id="1a70a-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a70a-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1a70a-114">Requirements</span></span>  
 <span data-ttu-id="1a70a-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a70a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a70a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a70a-116">See also</span></span>
- [<span data-ttu-id="1a70a-117">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="1a70a-117">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
