---
title: ICLRRuntimeInfo::GetVersionString – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetVersionString
helpviewer_keywords:
- ICLRRuntimeInfo::GetVersionString method [.NET Framework hosting]
- GetVersionString method, ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 98b097ef-2276-4dd9-8551-b03c972e8179
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a886106e5da49e7124dac5c8ea7416859aa441da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929843"
---
# <a name="iclrruntimeinfogetversionstring-method"></a><span data-ttu-id="3aed8-102">ICLRRuntimeInfo::GetVersionString – metoda</span><span class="sxs-lookup"><span data-stu-id="3aed8-102">ICLRRuntimeInfo::GetVersionString Method</span></span>
<span data-ttu-id="3aed8-103">Získá informace o verzi modulu CLR (Common Language Runtime) přidružené k danému rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3aed8-103">Gets common language runtime (CLR) version information associated with a given [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="3aed8-104">Tato metoda nahrazuje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="3aed8-104">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="3aed8-105">GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="3aed8-105">GetRequestedRuntimeInfo</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
  
- [<span data-ttu-id="3aed8-106">GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="3aed8-106">GetRequestedRuntimeVersion</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="3aed8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3aed8-107">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3aed8-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="3aed8-108">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="3aed8-109">mimo Verze kompilace .NET Framework ve formátu "v*A*. *B* [. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="3aed8-109">[out] The .NET Framework compilation version in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="3aed8-110">A, *B*a *X* jsou desítková čísla, která odpovídají hlavní verzi, dílčí verzi a číslo buildu.</span><span class="sxs-lookup"><span data-stu-id="3aed8-110">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="3aed8-111">*X* je volitelné.</span><span class="sxs-lookup"><span data-stu-id="3aed8-111">*X* is optional.</span></span> <span data-ttu-id="3aed8-112">Pokud není k dispozici *X* , neexistuje žádná koncová tečka.</span><span class="sxs-lookup"><span data-stu-id="3aed8-112">If *X* is not present, there is no trailing period.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3aed8-113">Tento parametr se musí shodovat s názvem adresáře pro verzi .NET Framework, jak se zobrazuje v části C:\Windows\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="3aed8-113">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="3aed8-114">Příklady hodnot jsou "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" a "v 4.0". *x*, kde *x* závisí na nainstalovaném čísle sestavení.</span><span class="sxs-lookup"><span data-stu-id="3aed8-114">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*x*", where *x* depends on the build number installed.</span></span> <span data-ttu-id="3aed8-115">Všimněte si, že předpona "v" je povinná.</span><span class="sxs-lookup"><span data-stu-id="3aed8-115">Note that the "v" prefix is mandatory.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="3aed8-116">[in, out] Určuje velikost `pwzBuffer` pro zamezení přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="3aed8-116">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="3aed8-117">Pokud `pwzBuffer` `pchBuffer` je `null`, vrátí požadovanou Velikost`pwzBuffer` pro, aby bylo možné předběžné přidělení.</span><span class="sxs-lookup"><span data-stu-id="3aed8-117">If `pwzBuffer` is `null`, `pchBuffer` returns the required size of `pwzBuffer` to allow preallocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3aed8-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3aed8-118">Return Value</span></span>  
 <span data-ttu-id="3aed8-119">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="3aed8-119">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3aed8-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3aed8-120">HRESULT</span></span>|<span data-ttu-id="3aed8-121">Popis</span><span class="sxs-lookup"><span data-stu-id="3aed8-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3aed8-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="3aed8-122">S_OK</span></span>|<span data-ttu-id="3aed8-123">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="3aed8-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="3aed8-124">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="3aed8-124">E_POINTER</span></span>|<span data-ttu-id="3aed8-125">`pwzBuffer`nebo `pchBuffer` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="3aed8-125">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3aed8-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3aed8-126">Requirements</span></span>  
 <span data-ttu-id="3aed8-127">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3aed8-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3aed8-128">**Hlaviček** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="3aed8-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3aed8-129">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3aed8-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3aed8-130">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3aed8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aed8-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3aed8-131">See also</span></span>

- [<span data-ttu-id="3aed8-132">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3aed8-132">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="3aed8-133">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="3aed8-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="3aed8-134">Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5</span><span class="sxs-lookup"><span data-stu-id="3aed8-134">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="3aed8-135">Hostování</span><span class="sxs-lookup"><span data-stu-id="3aed8-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
