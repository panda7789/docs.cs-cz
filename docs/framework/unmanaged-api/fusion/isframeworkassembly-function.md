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
ms.openlocfilehash: c3fd130759ab11b54b597d5c099c33dab93070ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429247"
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="c147e-102">IsFrameworkAssembly – funkce</span><span class="sxs-lookup"><span data-stu-id="c147e-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="c147e-103">Získá hodnotu, která určuje, jestli je zadané sestavení spravovaný.</span><span class="sxs-lookup"><span data-stu-id="c147e-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c147e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c147e-104">Syntax</span></span>  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c147e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c147e-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="c147e-106">[v] Název sestavení, které chcete zkontrolovat.</span><span class="sxs-lookup"><span data-stu-id="c147e-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="c147e-107">[out] Logická hodnota, která určuje, jestli je sestavení spravuje.</span><span class="sxs-lookup"><span data-stu-id="c147e-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="c147e-108">[v] Uncanonicalized řetězec, který obsahuje jedinečné identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="c147e-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="c147e-109">[v] Velikost `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="c147e-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c147e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c147e-110">Remarks</span></span>  
 <span data-ttu-id="c147e-111">`pwzAssemblyReference` Parametr je ukazatel na řetězec znaků, který obsahuje název sestavení.</span><span class="sxs-lookup"><span data-stu-id="c147e-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="c147e-112">Pokud je toto sestavení součástí rozhraní .NET Framework `pbIsFrameworkAssembly` parametr bude obsahovat logickou hodnotu z `true`.</span><span class="sxs-lookup"><span data-stu-id="c147e-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="c147e-113">Pokud pojmenovaný sestavení není součástí rozhraní .NET Framework, nebo pokud `pwzAssemblyReference` parametr není název sestavení, `pbIsFrameworkAssembly` bude obsahovat logickou hodnotu z `false`.</span><span class="sxs-lookup"><span data-stu-id="c147e-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c147e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c147e-114">Requirements</span></span>  
 <span data-ttu-id="c147e-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c147e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c147e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c147e-116">See Also</span></span>  
 [<span data-ttu-id="c147e-117">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="c147e-117">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
