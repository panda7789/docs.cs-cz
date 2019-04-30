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
ms.openlocfilehash: a6c715183d3ae04130b729a9680335d65959836a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946728"
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="d44d7-102">IsFrameworkAssembly – funkce</span><span class="sxs-lookup"><span data-stu-id="d44d7-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="d44d7-103">Získá hodnotu, která určuje, zda se spravuje zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="d44d7-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d44d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d44d7-104">Syntax</span></span>  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="d44d7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d44d7-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="d44d7-106">[in] Název sestavení ke kontrole.</span><span class="sxs-lookup"><span data-stu-id="d44d7-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="d44d7-107">[out] Logická hodnota, která určuje, jestli je spravované sestavení.</span><span class="sxs-lookup"><span data-stu-id="d44d7-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="d44d7-108">[in] Uncanonicalized řetězec, který obsahuje jedinečné identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="d44d7-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="d44d7-109">[in] Velikost `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="d44d7-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d44d7-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d44d7-110">Remarks</span></span>  
 <span data-ttu-id="d44d7-111">`pwzAssemblyReference` Parametrem je ukazatel na řetězec znaků, který obsahuje název sestavení.</span><span class="sxs-lookup"><span data-stu-id="d44d7-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="d44d7-112">Pokud je toto sestavení součástí .NET Framework `pbIsFrameworkAssembly` parametr bude obsahovat hodnotu typu Boolean `true`.</span><span class="sxs-lookup"><span data-stu-id="d44d7-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="d44d7-113">Pokud pojmenované sestavení není součástí rozhraní .NET Framework, nebo pokud `pwzAssemblyReference` sestavení, nikoli název parametru `pbIsFrameworkAssembly` bude obsahovat hodnotu typu Boolean `false`.</span><span class="sxs-lookup"><span data-stu-id="d44d7-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d44d7-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d44d7-114">Requirements</span></span>  
 <span data-ttu-id="d44d7-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d44d7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d44d7-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d44d7-116">See also</span></span>

- [<span data-ttu-id="d44d7-117">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="d44d7-117">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
