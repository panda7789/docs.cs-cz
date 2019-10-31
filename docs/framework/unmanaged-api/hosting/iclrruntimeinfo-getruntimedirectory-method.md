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
ms.openlocfilehash: b0a2e5f259fe1ee566f9cc25152b2d2a1f740bea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120339"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="ca846-102">ICLRRuntimeInfo::GetRuntimeDirectory – metoda</span><span class="sxs-lookup"><span data-stu-id="ca846-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>
<span data-ttu-id="ca846-103">Získá instalační adresář modulu CLR (Common Language Runtime) přidruženého k tomuto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ca846-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="ca846-104">Tato metoda nahrazuje funkci [GetCORSystemDirectory –](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) , která je k dispozici v .NET Framework verzích 2,0, 3,0 a 3,5.</span><span class="sxs-lookup"><span data-stu-id="ca846-104">This method supersedes the [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca846-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca846-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca846-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ca846-106">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="ca846-107">mimo Vrátí instalační adresář CLR.</span><span class="sxs-lookup"><span data-stu-id="ca846-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="ca846-108">Cesta instalace je plně kvalifikovaná; například "c:\Windows\Microsoft.NET\Framework\v1.0.3705\\".</span><span class="sxs-lookup"><span data-stu-id="ca846-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="ca846-109">[in, out] Určuje velikost `pwzBuffer`, aby se předešlo přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ca846-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="ca846-110">Pokud je `pwzBuffer` null, `pchBuffer` vrátí požadovanou velikost `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="ca846-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca846-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ca846-111">Return Value</span></span>  
 <span data-ttu-id="ca846-112">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="ca846-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ca846-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ca846-113">HRESULT</span></span>|<span data-ttu-id="ca846-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ca846-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca846-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="ca846-115">S_OK</span></span>|<span data-ttu-id="ca846-116">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="ca846-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="ca846-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="ca846-117">E_POINTER</span></span>|<span data-ttu-id="ca846-118">`pwzBuffer` nebo `pchBuffer` je null.</span><span class="sxs-lookup"><span data-stu-id="ca846-118">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca846-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ca846-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca846-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ca846-120">Requirements</span></span>  
 <span data-ttu-id="ca846-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca846-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca846-122">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="ca846-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ca846-123">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ca846-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca846-124">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca846-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca846-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca846-125">See also</span></span>

- [<span data-ttu-id="ca846-126">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca846-126">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="ca846-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="ca846-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
