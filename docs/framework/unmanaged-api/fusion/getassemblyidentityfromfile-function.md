---
title: "GetAssemblyIdentityFromFile – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: COM
f1_keywords: GetAssemblyIdentityFromFile
helpviewer_keywords: GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 56d7fb4ee74e40ecd29ee276665ff43ab9fd56be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="a7efd-102">GetAssemblyIdentityFromFile – funkce</span><span class="sxs-lookup"><span data-stu-id="a7efd-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="a7efd-103">Získá odkazy `IUnknown` objekt se zadaným `IID` v sestavení v zadaná cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="a7efd-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7efd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7efd-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7efd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7efd-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="a7efd-106">[v] Platná cesta k požadované sestavení.</span><span class="sxs-lookup"><span data-stu-id="a7efd-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="a7efd-107">[v] `IID` Rozhraní vrátit.</span><span class="sxs-lookup"><span data-stu-id="a7efd-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="a7efd-108">[out] Ukazatel vrácený rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a7efd-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7efd-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a7efd-109">Requirements</span></span>  
 <span data-ttu-id="a7efd-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7efd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7efd-111">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="a7efd-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a7efd-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7efd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7efd-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7efd-113">See Also</span></span>  
 <span data-ttu-id="a7efd-114"><<!--zzxref:IUnknown --> `IUnknown`></span><span class="sxs-lookup"><span data-stu-id="a7efd-114"><<!--zzxref:IUnknown --> `IUnknown`></span></span>  
 [<span data-ttu-id="a7efd-115">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="a7efd-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
