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
ms.openlocfilehash: 9f3374553df02193a6b726f37a53a929533e86cd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="7c62b-102">GetAssemblyIdentityFromFile – funkce</span><span class="sxs-lookup"><span data-stu-id="7c62b-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="7c62b-103">Získá odkazy `IUnknown` objekt se zadaným `IID` v sestavení v zadaná cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="7c62b-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c62b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c62b-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c62b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c62b-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="7c62b-106">[v] Platná cesta k požadované sestavení.</span><span class="sxs-lookup"><span data-stu-id="7c62b-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="7c62b-107">[v] `IID` Rozhraní vrátit.</span><span class="sxs-lookup"><span data-stu-id="7c62b-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="7c62b-108">[out] Ukazatel vrácený rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7c62b-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c62b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c62b-109">Requirements</span></span>  
 <span data-ttu-id="7c62b-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c62b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c62b-111">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="7c62b-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7c62b-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c62b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c62b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c62b-113">See Also</span></span>  
 <span data-ttu-id="7c62b-114"><<!--zzxref:IUnknown --> `IUnknown`></span><span class="sxs-lookup"><span data-stu-id="7c62b-114"><<!--zzxref:IUnknown --> `IUnknown`></span></span>  
 [<span data-ttu-id="7c62b-115">Fúze globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="7c62b-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
