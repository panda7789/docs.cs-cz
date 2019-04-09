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
ms.openlocfilehash: 5c09f57ad805b4ba17b4bdafd3ced533199277a0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196681"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="18ff4-102">ICLRRuntimeInfo::GetRuntimeDirectory – metoda</span><span class="sxs-lookup"><span data-stu-id="18ff4-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>
<span data-ttu-id="18ff4-103">Načte instalační adresář modulu common language runtime (CLR) spojený s tímto rozhraním.</span><span class="sxs-lookup"><span data-stu-id="18ff4-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="18ff4-104">Tato metoda nahrazuje [getcorsystemdirectory –](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) funkce k dispozici v rozhraní .NET Framework verze 2.0, 3.0 a 3.5.</span><span class="sxs-lookup"><span data-stu-id="18ff4-104">This method supersedes the [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18ff4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18ff4-105">Syntax</span></span>  
  
```  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18ff4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="18ff4-106">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="18ff4-107">[out] Vrátí instalační adresář modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="18ff4-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="18ff4-108">Cesta instalace je plně kvalifikovaný; například "c:\windows\microsoft.net\framework\v1.0.3705\\".</span><span class="sxs-lookup"><span data-stu-id="18ff4-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="18ff4-109">[out v] Určuje velikost `pwzBuffer` , aby přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="18ff4-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="18ff4-110">Pokud `pwzBuffer` má hodnotu null, `pchBuffer` vrátí velikost požadované `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="18ff4-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18ff4-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="18ff4-111">Return Value</span></span>  
 <span data-ttu-id="18ff4-112">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="18ff4-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="18ff4-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="18ff4-113">HRESULT</span></span>|<span data-ttu-id="18ff4-114">Popis</span><span class="sxs-lookup"><span data-stu-id="18ff4-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="18ff4-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="18ff4-115">S_OK</span></span>|<span data-ttu-id="18ff4-116">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="18ff4-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="18ff4-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="18ff4-117">E_POINTER</span></span>|`pwzBuffer` <span data-ttu-id="18ff4-118">nebo `pchBuffer` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="18ff4-118">or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18ff4-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18ff4-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18ff4-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="18ff4-120">Requirements</span></span>  
 <span data-ttu-id="18ff4-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18ff4-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18ff4-122">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="18ff4-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="18ff4-123">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="18ff4-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="18ff4-124">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="18ff4-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="18ff4-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18ff4-125">See also</span></span>

- [<span data-ttu-id="18ff4-126">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18ff4-126">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="18ff4-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="18ff4-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
