---
title: GetAssemblyIdentityFromFile – funkce
ms.date: 03/30/2017
api_name:
- GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyIdentityFromFile
helpviewer_keywords:
- GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6dfb0b404413351761d269c800be19e75acfb41f
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752275"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="c9642-102">GetAssemblyIdentityFromFile – funkce</span><span class="sxs-lookup"><span data-stu-id="c9642-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="c9642-103">Získá ukazatel `IUnknown` objekt se zadaným `IID` v sestavení v cestě zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="c9642-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9642-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9642-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9642-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9642-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="c9642-106">[in] Platná cesta k požadované sestavení.</span><span class="sxs-lookup"><span data-stu-id="c9642-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="c9642-107">[in] `IID` Rozhraní k vrácení.</span><span class="sxs-lookup"><span data-stu-id="c9642-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="c9642-108">[out] Vrácený ukazatel rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c9642-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9642-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9642-109">Requirements</span></span>  
 <span data-ttu-id="c9642-110">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9642-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9642-111">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="c9642-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c9642-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9642-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9642-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9642-113">See Also</span></span>  
 [<span data-ttu-id="c9642-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="c9642-114">IUnknown</span></span>](/cpp/atl/iunknown)  
 [<span data-ttu-id="c9642-115">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="c9642-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
