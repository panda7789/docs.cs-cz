---
title: "IsFrameworkAssembly – funkce"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aa077ce13031772ec2ea20708c1dbd29da02d32a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="25db9-102">IsFrameworkAssembly – funkce</span><span class="sxs-lookup"><span data-stu-id="25db9-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="25db9-103">Získá hodnotu, která určuje, jestli je zadané sestavení spravovaný.</span><span class="sxs-lookup"><span data-stu-id="25db9-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25db9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25db9-104">Syntax</span></span>  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25db9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25db9-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="25db9-106">[v] Název sestavení, které chcete zkontrolovat.</span><span class="sxs-lookup"><span data-stu-id="25db9-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="25db9-107">[out] Logická hodnota, která určuje, jestli je sestavení spravuje.</span><span class="sxs-lookup"><span data-stu-id="25db9-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="25db9-108">[v] Uncanonicalized řetězec, který obsahuje jedinečné identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="25db9-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="25db9-109">[v] Velikost `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="25db9-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25db9-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25db9-110">Remarks</span></span>  
 <span data-ttu-id="25db9-111">`pwzAssemblyReference` Parametr je ukazatel na řetězec znaků, který obsahuje název sestavení.</span><span class="sxs-lookup"><span data-stu-id="25db9-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="25db9-112">Pokud je toto sestavení součástí rozhraní .NET Framework `pbIsFrameworkAssembly` parametr bude obsahovat logickou hodnotu z `true`.</span><span class="sxs-lookup"><span data-stu-id="25db9-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="25db9-113">Pokud pojmenovaný sestavení není součástí rozhraní .NET Framework, nebo pokud `pwzAssemblyReference` parametr není název sestavení, `pbIsFrameworkAssembly` bude obsahovat logickou hodnotu z `false`.</span><span class="sxs-lookup"><span data-stu-id="25db9-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25db9-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25db9-114">Requirements</span></span>  
 <span data-ttu-id="25db9-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25db9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25db9-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="25db9-116">See Also</span></span>  
 [<span data-ttu-id="25db9-117">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="25db9-117">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
