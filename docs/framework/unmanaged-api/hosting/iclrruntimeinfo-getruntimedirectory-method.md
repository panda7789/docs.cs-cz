---
title: ICLRRuntimeInfo::GetRuntimeDirectory – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetRuntimeDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 159e9b3d81db5b416eb98e1b7587712ba14033c5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466970"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="97149-102">ICLRRuntimeInfo::GetRuntimeDirectory – metoda</span><span class="sxs-lookup"><span data-stu-id="97149-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>
<span data-ttu-id="97149-103">Načte instalační adresář modulu common language runtime (CLR) spojený s tímto rozhraním.</span><span class="sxs-lookup"><span data-stu-id="97149-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="97149-104">Tato metoda nahrazuje [getcorsystemdirectory –](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) funkce k dispozici v rozhraní .NET Framework verze 2.0, 3.0 a 3.5.</span><span class="sxs-lookup"><span data-stu-id="97149-104">This method supersedes the [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97149-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97149-105">Syntax</span></span>  
  
```  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97149-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="97149-106">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="97149-107">[out] Vrátí instalační adresář modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="97149-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="97149-108">Cesta instalace je plně kvalifikovaný; například "c:\windows\microsoft.net\framework\v1.0.3705\\".</span><span class="sxs-lookup"><span data-stu-id="97149-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="97149-109">[out v] Určuje velikost `pwzBuffer` , aby přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="97149-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="97149-110">Pokud `pwzBuffer` má hodnotu null, `pchBuffer` vrátí velikost požadované `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="97149-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97149-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="97149-111">Return Value</span></span>  
 <span data-ttu-id="97149-112">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="97149-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="97149-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="97149-113">HRESULT</span></span>|<span data-ttu-id="97149-114">Popis</span><span class="sxs-lookup"><span data-stu-id="97149-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="97149-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="97149-115">S_OK</span></span>|<span data-ttu-id="97149-116">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="97149-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="97149-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="97149-117">E_POINTER</span></span>|<span data-ttu-id="97149-118">`pwzBuffer` nebo `pchBuffer` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="97149-118">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97149-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="97149-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97149-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="97149-120">Requirements</span></span>  
 <span data-ttu-id="97149-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97149-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97149-122">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="97149-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="97149-123">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="97149-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97149-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97149-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97149-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97149-125">See also</span></span>
- [<span data-ttu-id="97149-126">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="97149-126">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="97149-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="97149-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
