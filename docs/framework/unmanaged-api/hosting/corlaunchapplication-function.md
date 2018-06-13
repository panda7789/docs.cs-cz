---
title: CorLaunchApplication – funkce
ms.date: 03/30/2017
api_name:
- CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CorLaunchApplication
helpviewer_keywords:
- CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a53b0a9cdcec33846f9d491e7d6567bcf9235b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428759"
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="81082-102">CorLaunchApplication – funkce</span><span class="sxs-lookup"><span data-stu-id="81082-102">CorLaunchApplication Function</span></span>
<span data-ttu-id="81082-103">Spuštění aplikace v zadané síťové cestě, pomocí zadané manifesty a ostatní data aplikací.</span><span class="sxs-lookup"><span data-stu-id="81082-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="81082-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="81082-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81082-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81082-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="81082-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="81082-106">Parameters</span></span>  
 `dwClickOnceHost`  
 <span data-ttu-id="81082-107">[v] Hodnota [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) výčet, který určuje typ hostitele, který je spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="81082-107">[in] A value of the [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="81082-108">[v] Úplný název aplikace, která je právě spuštěna.</span><span class="sxs-lookup"><span data-stu-id="81082-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="81082-109">[v] Počet manifestu cesty pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="81082-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="81082-110">[v] Pole řetězců, z nichž každý Určuje cestu k manifestu pro aplikace, která je právě spuštěna.</span><span class="sxs-lookup"><span data-stu-id="81082-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="81082-111">[v] Počet položek dat aktivace pro aplikaci, která je právě spuštěna.</span><span class="sxs-lookup"><span data-stu-id="81082-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="81082-112">[v] Pole řetězců, z nichž každý je aktivace položky dat pro aplikaci, která je právě spuštěna.</span><span class="sxs-lookup"><span data-stu-id="81082-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="81082-113">[out] Ukazatel na informace o procesu, ve kterém se načetl aplikace.</span><span class="sxs-lookup"><span data-stu-id="81082-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81082-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="81082-114">Requirements</span></span>  
 <span data-ttu-id="81082-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81082-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81082-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="81082-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81082-117">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="81082-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81082-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81082-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81082-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="81082-119">See Also</span></span>  
 [<span data-ttu-id="81082-120">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="81082-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
