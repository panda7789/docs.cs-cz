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
ms.openlocfilehash: 20ea800b86a169eff984b6068db3e9887235a034
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496973"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="60820-102">GetAssemblyIdentityFromFile – funkce</span><span class="sxs-lookup"><span data-stu-id="60820-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="60820-103">Získá ukazatel `IUnknown` objekt se zadaným `IID` v sestavení v cestě zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="60820-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60820-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60820-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="60820-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60820-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="60820-106">[in] Platná cesta k požadované sestavení.</span><span class="sxs-lookup"><span data-stu-id="60820-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="60820-107">[in] `IID` Rozhraní k vrácení.</span><span class="sxs-lookup"><span data-stu-id="60820-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="60820-108">[out] Vrácený ukazatel rozhraní.</span><span class="sxs-lookup"><span data-stu-id="60820-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60820-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60820-109">Requirements</span></span>  
 <span data-ttu-id="60820-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60820-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60820-111">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="60820-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="60820-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60820-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60820-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60820-113">See also</span></span>
- [<span data-ttu-id="60820-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="60820-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="60820-115">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="60820-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
