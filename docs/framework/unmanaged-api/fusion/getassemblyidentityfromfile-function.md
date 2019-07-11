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
ms.openlocfilehash: 581c675cfb69503e6366471a469ffed1a2d13b1a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745229"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="f0eeb-102">GetAssemblyIdentityFromFile – funkce</span><span class="sxs-lookup"><span data-stu-id="f0eeb-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="f0eeb-103">Získá ukazatel `IUnknown` objekt se zadaným `IID` v sestavení v cestě zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="f0eeb-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0eeb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0eeb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0eeb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0eeb-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="f0eeb-106">[in] Platná cesta k požadované sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0eeb-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="f0eeb-107">[in] `IID` Rozhraní k vrácení.</span><span class="sxs-lookup"><span data-stu-id="f0eeb-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="f0eeb-108">[out] Vrácený ukazatel rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f0eeb-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0eeb-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f0eeb-109">Requirements</span></span>  
 <span data-ttu-id="f0eeb-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0eeb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0eeb-111">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="f0eeb-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f0eeb-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0eeb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0eeb-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0eeb-113">See also</span></span>

- [<span data-ttu-id="f0eeb-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="f0eeb-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="f0eeb-115">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="f0eeb-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
