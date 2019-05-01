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
ms.openlocfilehash: 4c997ab107ba3ceb7773bc9235b9c9dcd4d97df8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985787"
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="537ab-102">CorLaunchApplication – funkce</span><span class="sxs-lookup"><span data-stu-id="537ab-102">CorLaunchApplication Function</span></span>
<span data-ttu-id="537ab-103">Spustí aplikaci v zadané síťové cestě pomocí zadaných manifestů a dalších dat aplikací.</span><span class="sxs-lookup"><span data-stu-id="537ab-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="537ab-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="537ab-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="537ab-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="537ab-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="537ab-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="537ab-106">Parameters</span></span>  
 `dwClickOnceHost`  
 <span data-ttu-id="537ab-107">[in] Hodnota [host_type –](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) výčet, který určuje typ hostitele, který se spuštěním aplikace.</span><span class="sxs-lookup"><span data-stu-id="537ab-107">[in] A value of the [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="537ab-108">[in] Celý název aplikace, která se spustí.</span><span class="sxs-lookup"><span data-stu-id="537ab-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="537ab-109">[in] Počet cesty k manifestu aplikace.</span><span class="sxs-lookup"><span data-stu-id="537ab-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="537ab-110">[in] Pole řetězců, z nichž každý Určuje cestu k manifestu pro aplikaci, která se spustí.</span><span class="sxs-lookup"><span data-stu-id="537ab-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="537ab-111">[in] Počet datových položek aktivace pro aplikaci, která se spustí.</span><span class="sxs-lookup"><span data-stu-id="537ab-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="537ab-112">[in] Pole řetězců, z nichž každý je aktivace položka dat pro aplikace, která se spustí.</span><span class="sxs-lookup"><span data-stu-id="537ab-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="537ab-113">[out] Ukazatel na informace o procesu, ve kterém se načetl aplikace.</span><span class="sxs-lookup"><span data-stu-id="537ab-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="537ab-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="537ab-114">Requirements</span></span>  
 <span data-ttu-id="537ab-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="537ab-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="537ab-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="537ab-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="537ab-117">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="537ab-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="537ab-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="537ab-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="537ab-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="537ab-119">See also</span></span>

- [<span data-ttu-id="537ab-120">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="537ab-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
