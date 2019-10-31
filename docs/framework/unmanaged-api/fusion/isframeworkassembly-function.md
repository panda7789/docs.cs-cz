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
ms.openlocfilehash: e30b6f2d2254d2d107c4c82a2c5664850ce6ec23
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123072"
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="2547b-102">IsFrameworkAssembly – funkce</span><span class="sxs-lookup"><span data-stu-id="2547b-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="2547b-103">Získá hodnotu, která označuje, zda je zadané sestavení spravováno.</span><span class="sxs-lookup"><span data-stu-id="2547b-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2547b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2547b-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="2547b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2547b-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="2547b-106">pro Název sestavení, které má být zkontrolováno.</span><span class="sxs-lookup"><span data-stu-id="2547b-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="2547b-107">mimo Logická hodnota, která určuje, zda je sestavení spravováno.</span><span class="sxs-lookup"><span data-stu-id="2547b-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="2547b-108">pro Nekanonický řetězec, který obsahuje jedinečnou identitu sestavení.</span><span class="sxs-lookup"><span data-stu-id="2547b-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="2547b-109">pro Velikost `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="2547b-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2547b-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2547b-110">Remarks</span></span>  
 <span data-ttu-id="2547b-111">Parametr `pwzAssemblyReference` je ukazatel na řetězec znaků, který obsahuje název sestavení.</span><span class="sxs-lookup"><span data-stu-id="2547b-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="2547b-112">Pokud je toto sestavení součástí .NET Framework, parametr `pbIsFrameworkAssembly` bude obsahovat logickou hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="2547b-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="2547b-113">Pokud pojmenované sestavení není součástí .NET Framework, nebo pokud parametr `pwzAssemblyReference` nejmenuje sestavení, `pbIsFrameworkAssembly` bude obsahovat logickou hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="2547b-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2547b-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2547b-114">Requirements</span></span>  
 <span data-ttu-id="2547b-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2547b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2547b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2547b-116">See also</span></span>

- [<span data-ttu-id="2547b-117">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="2547b-117">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
