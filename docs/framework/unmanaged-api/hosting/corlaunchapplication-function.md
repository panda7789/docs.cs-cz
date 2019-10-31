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
ms.openlocfilehash: e01698d2d8491b2496bb664c13dca97964cd1481
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136948"
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="1da00-102">CorLaunchApplication – funkce</span><span class="sxs-lookup"><span data-stu-id="1da00-102">CorLaunchApplication Function</span></span>
<span data-ttu-id="1da00-103">Spustí aplikaci v zadané síťové cestě s použitím zadaných manifestů a dalších aplikačních dat.</span><span class="sxs-lookup"><span data-stu-id="1da00-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="1da00-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="1da00-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1da00-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1da00-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="1da00-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1da00-106">Parameters</span></span>  
 `dwClickOnceHost`  
 <span data-ttu-id="1da00-107">pro Hodnota výčtu [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) , která určuje typ hostitele, který spouští aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1da00-107">[in] A value of the [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="1da00-108">pro Úplný název aplikace, která se spouští.</span><span class="sxs-lookup"><span data-stu-id="1da00-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="1da00-109">pro Počet cest k manifestu pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1da00-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="1da00-110">pro Pole řetězců, z nichž každý Určuje cestu k manifestu pro aplikaci, která se právě spouští.</span><span class="sxs-lookup"><span data-stu-id="1da00-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="1da00-111">pro Počet položek aktivačních dat pro aplikaci, která se spouští.</span><span class="sxs-lookup"><span data-stu-id="1da00-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="1da00-112">pro Pole řetězců, z nichž každá představuje položku aktivační data pro aplikaci, která se spouští.</span><span class="sxs-lookup"><span data-stu-id="1da00-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="1da00-113">mimo Ukazatel na informace o procesu, ve kterém byla aplikace načtena.</span><span class="sxs-lookup"><span data-stu-id="1da00-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1da00-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1da00-114">Requirements</span></span>  
 <span data-ttu-id="1da00-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1da00-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1da00-116">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1da00-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1da00-117">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1da00-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1da00-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1da00-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1da00-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1da00-119">See also</span></span>

- [<span data-ttu-id="1da00-120">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="1da00-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
