---
title: "IsFrameworkAssembly – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IsFrameworkAssembly
api_location: fusion.dll
api_type: COM
f1_keywords: IsFrameworkAssembly
helpviewer_keywords: IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 216a7221550cb6345b29b5ed9e45b13ce40eadf4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="32545-102">IsFrameworkAssembly – funkce</span><span class="sxs-lookup"><span data-stu-id="32545-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="32545-103">Získá hodnotu, která určuje, jestli je zadané sestavení spravovaný.</span><span class="sxs-lookup"><span data-stu-id="32545-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32545-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32545-104">Syntax</span></span>  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32545-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32545-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="32545-106">[v] Název sestavení, které chcete zkontrolovat.</span><span class="sxs-lookup"><span data-stu-id="32545-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="32545-107">[out] Logická hodnota, která určuje, jestli je sestavení spravuje.</span><span class="sxs-lookup"><span data-stu-id="32545-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="32545-108">[v] Uncanonicalized řetězec, který obsahuje jedinečné identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="32545-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="32545-109">[v] Velikost `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="32545-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32545-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="32545-110">Remarks</span></span>  
 <span data-ttu-id="32545-111">`pwzAssemblyReference` Parametr je ukazatel na řetězec znaků, který obsahuje název sestavení.</span><span class="sxs-lookup"><span data-stu-id="32545-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="32545-112">Pokud je toto sestavení součástí rozhraní .NET Framework `pbIsFrameworkAssembly` parametr bude obsahovat logickou hodnotu z `true`.</span><span class="sxs-lookup"><span data-stu-id="32545-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="32545-113">Pokud pojmenovaný sestavení není součástí rozhraní .NET Framework, nebo pokud `pwzAssemblyReference` parametr není název sestavení, `pbIsFrameworkAssembly` bude obsahovat logickou hodnotu z `false`.</span><span class="sxs-lookup"><span data-stu-id="32545-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32545-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="32545-114">Requirements</span></span>  
 <span data-ttu-id="32545-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32545-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32545-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="32545-116">See Also</span></span>  
 [<span data-ttu-id="32545-117">Fúze globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="32545-117">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
