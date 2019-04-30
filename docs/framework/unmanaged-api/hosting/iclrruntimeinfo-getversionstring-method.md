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
ms.openlocfilehash: d6e320936430307dab066eecc835ac5c84bd22bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771696"
---
# <a name="iclrruntimeinfogetversionstring-method"></a><span data-ttu-id="0768d-102">ICLRRuntimeInfo::GetVersionString – metoda</span><span class="sxs-lookup"><span data-stu-id="0768d-102">ICLRRuntimeInfo::GetVersionString Method</span></span>
<span data-ttu-id="0768d-103">Získá common language runtime (CLR) informace o verzi přidružené danou [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0768d-103">Gets common language runtime (CLR) version information associated with a given [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="0768d-104">Tato metoda nahrazuje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="0768d-104">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="0768d-105">GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="0768d-105">GetRequestedRuntimeInfo</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
  
- [<span data-ttu-id="0768d-106">GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="0768d-106">GetRequestedRuntimeVersion</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="0768d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0768d-107">Syntax</span></span>  
  
```  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0768d-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="0768d-108">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="0768d-109">[out] Kompilace rozhraní .NET Framework verze ve formátu "v*A*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="0768d-109">[out] The .NET Framework compilation version in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="0768d-110">*A*, *B*, a *X* jsou desetinná čísla, která odpovídá hlavní verze, podverze a číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="0768d-110">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="0768d-111">*X* je volitelný.</span><span class="sxs-lookup"><span data-stu-id="0768d-111">*X* is optional.</span></span> <span data-ttu-id="0768d-112">Pokud *X* není k dispozici není žádné koncové tečky.</span><span class="sxs-lookup"><span data-stu-id="0768d-112">If *X* is not present, there is no trailing period.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0768d-113">Tento parametr musí odpovídat názvu adresáře pro verzi rozhraní .NET Framework, jak se zobrazí v části C:\Windows\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="0768d-113">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="0768d-114">Příklad hodnoty jsou "v1.0.3705", "v1.1.4322", "v2.0.50727" a "v4.0. *x*", kde *x* závisí na číslo sestavení nainstalována.</span><span class="sxs-lookup"><span data-stu-id="0768d-114">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*x*", where *x* depends on the build number installed.</span></span> <span data-ttu-id="0768d-115">Všimněte si, že předpona "v" je povinný.</span><span class="sxs-lookup"><span data-stu-id="0768d-115">Note that the "v" prefix is mandatory.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="0768d-116">[out v] Určuje velikost `pwzBuffer` , aby přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="0768d-116">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="0768d-117">Pokud `pwzBuffer` je `null`, `pchBuffer` vrátí velikost požadované `pwzBuffer` povolit předběžné přidělování.</span><span class="sxs-lookup"><span data-stu-id="0768d-117">If `pwzBuffer` is `null`, `pchBuffer` returns the required size of `pwzBuffer` to allow preallocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0768d-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0768d-118">Return Value</span></span>  
 <span data-ttu-id="0768d-119">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="0768d-119">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0768d-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0768d-120">HRESULT</span></span>|<span data-ttu-id="0768d-121">Popis</span><span class="sxs-lookup"><span data-stu-id="0768d-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0768d-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="0768d-122">S_OK</span></span>|<span data-ttu-id="0768d-123">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="0768d-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="0768d-124">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="0768d-124">E_POINTER</span></span>|<span data-ttu-id="0768d-125">`pwzBuffer` nebo `pchBuffer` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="0768d-125">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0768d-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0768d-126">Requirements</span></span>  
 <span data-ttu-id="0768d-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0768d-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0768d-128">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="0768d-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0768d-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0768d-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0768d-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0768d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0768d-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0768d-131">See also</span></span>

- [<span data-ttu-id="0768d-132">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0768d-132">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="0768d-133">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="0768d-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="0768d-134">Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5</span><span class="sxs-lookup"><span data-stu-id="0768d-134">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="0768d-135">Hostování</span><span class="sxs-lookup"><span data-stu-id="0768d-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
