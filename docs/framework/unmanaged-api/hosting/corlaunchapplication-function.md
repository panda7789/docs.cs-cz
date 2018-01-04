---
title: "CorLaunchApplication – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type: COM
f1_keywords: CorLaunchApplication
helpviewer_keywords: CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bf4392f7b30a5faa1cb01e24f9262260d9c6e93a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="f6d39-102">CorLaunchApplication – funkce</span><span class="sxs-lookup"><span data-stu-id="f6d39-102">CorLaunchApplication Function</span></span>
<span data-ttu-id="f6d39-103">Spuštění aplikace v zadané síťové cestě, pomocí zadané manifesty a ostatní data aplikací.</span><span class="sxs-lookup"><span data-stu-id="f6d39-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="f6d39-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f6d39-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6d39-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6d39-105">Syntax</span></span>  
  
```  
HRESULT CorLaunchApplication (  
    [in]  HOST_TYPE                dwClickOnceHost,  
    [in]  LPCWSTR                  pwzAppFullName,  
    [in]  DWORD                    dwManifestPaths,  
    [in]  LPCWSTR                 *ppwzManifestPaths,  
    [in]  DWORD                    dwActivationData,  
    [in]  LPCWSTR                 *ppwzActivationData,  
    [out] LPPROCESS_INFORMATION    lpProcessInformation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6d39-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6d39-106">Parameters</span></span>  
 `dwClickOnceHost`  
 <span data-ttu-id="f6d39-107">[v] Hodnota [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) výčet, který určuje typ hostitele, který je spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="f6d39-107">[in] A value of the [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="f6d39-108">[v] Úplný název aplikace, která je právě spuštěna.</span><span class="sxs-lookup"><span data-stu-id="f6d39-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="f6d39-109">[v] Počet manifestu cesty pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f6d39-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="f6d39-110">[v] Pole řetězců, z nichž každý Určuje cestu k manifestu pro aplikace, která je právě spuštěna.</span><span class="sxs-lookup"><span data-stu-id="f6d39-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="f6d39-111">[v] Počet položek dat aktivace pro aplikaci, která je právě spuštěna.</span><span class="sxs-lookup"><span data-stu-id="f6d39-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="f6d39-112">[v] Pole řetězců, z nichž každý je aktivace položky dat pro aplikaci, která je právě spuštěna.</span><span class="sxs-lookup"><span data-stu-id="f6d39-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="f6d39-113">[out] Ukazatel na informace o procesu, ve kterém se načetl aplikace.</span><span class="sxs-lookup"><span data-stu-id="f6d39-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6d39-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f6d39-114">Requirements</span></span>  
 <span data-ttu-id="f6d39-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6d39-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6d39-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f6d39-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f6d39-117">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6d39-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6d39-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6d39-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6d39-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6d39-119">See Also</span></span>  
 [<span data-ttu-id="f6d39-120">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="f6d39-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
