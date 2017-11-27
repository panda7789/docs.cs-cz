---
title: "ICLRRuntimeInfo::GetRuntimeDirectory – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.GetRuntimeDirectory
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ddaca8232f0b262377c7915852da89cecec09993
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="58896-102">ICLRRuntimeInfo::GetRuntimeDirectory – metoda</span><span class="sxs-lookup"><span data-stu-id="58896-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>
<span data-ttu-id="58896-103">Získá instalační adresář common language runtime (CLR) spojené s tímto rozhraním.</span><span class="sxs-lookup"><span data-stu-id="58896-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="58896-104">Tato metoda nahrazuje [getcorsystemdirectory –](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) funkce, které jsou k dispozici v rozhraní .NET Framework verze 2.0, 3.0 a 3.5.</span><span class="sxs-lookup"><span data-stu-id="58896-104">This method supersedes the [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58896-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58896-105">Syntax</span></span>  
  
```  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58896-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="58896-106">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="58896-107">[out] Vrátí instalační adresář modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="58896-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="58896-108">Cesta instalace je plně kvalifikovaný; například "c:\windows\microsoft.net\framework\v1.0.3705\\".</span><span class="sxs-lookup"><span data-stu-id="58896-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="58896-109">[ve out] Určuje velikost `pwzBuffer` předejdete přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="58896-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="58896-110">Pokud `pwzBuffer` má hodnotu null, `pchBuffer` vrátí požadovaná velikost `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="58896-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58896-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="58896-111">Return Value</span></span>  
 <span data-ttu-id="58896-112">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="58896-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="58896-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="58896-113">HRESULT</span></span>|<span data-ttu-id="58896-114">Popis</span><span class="sxs-lookup"><span data-stu-id="58896-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="58896-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="58896-115">S_OK</span></span>|<span data-ttu-id="58896-116">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="58896-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="58896-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="58896-117">E_POINTER</span></span>|<span data-ttu-id="58896-118">`pwzBuffer`nebo `pchBuffer` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="58896-118">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58896-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="58896-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58896-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="58896-120">Requirements</span></span>  
 <span data-ttu-id="58896-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58896-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58896-122">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="58896-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="58896-123">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="58896-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58896-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58896-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58896-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="58896-125">See Also</span></span>  
 [<span data-ttu-id="58896-126">Iclrruntimeinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="58896-126">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="58896-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="58896-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
