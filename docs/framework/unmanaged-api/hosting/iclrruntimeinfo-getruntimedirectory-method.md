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
ms.openlocfilehash: d744abf5c502e9b9510cf9fd6479149b6c2177cc
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762211"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="877d2-102">ICLRRuntimeInfo::GetRuntimeDirectory – metoda</span><span class="sxs-lookup"><span data-stu-id="877d2-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>
<span data-ttu-id="877d2-103">Získá instalační adresář modulu CLR (Common Language Runtime) přidruženého k tomuto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="877d2-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="877d2-104">Tato metoda nahrazuje funkci [GetCORSystemDirectory –](getcorsystemdirectory-function.md) , která je k dispozici v .NET Framework verzích 2,0, 3,0 a 3,5.</span><span class="sxs-lookup"><span data-stu-id="877d2-104">This method supersedes the [GetCORSystemDirectory](getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="877d2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="877d2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="877d2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="877d2-106">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="877d2-107">mimo Vrátí instalační adresář CLR.</span><span class="sxs-lookup"><span data-stu-id="877d2-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="877d2-108">Cesta instalace je plně kvalifikovaná; například "c:\Windows\Microsoft.NET\Framework\v1.0.3705 \\ ".</span><span class="sxs-lookup"><span data-stu-id="877d2-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="877d2-109">[in, out] Určuje velikost `pwzBuffer` pro zamezení přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="877d2-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="877d2-110">Pokud `pwzBuffer` je null, `pchBuffer` vrátí požadovanou velikost `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="877d2-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="877d2-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="877d2-111">Return Value</span></span>  
 <span data-ttu-id="877d2-112">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="877d2-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="877d2-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="877d2-113">HRESULT</span></span>|<span data-ttu-id="877d2-114">Popis</span><span class="sxs-lookup"><span data-stu-id="877d2-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="877d2-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="877d2-115">S_OK</span></span>|<span data-ttu-id="877d2-116">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="877d2-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="877d2-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="877d2-117">E_POINTER</span></span>|<span data-ttu-id="877d2-118">`pwzBuffer`nebo `pchBuffer` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="877d2-118">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="877d2-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="877d2-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="877d2-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="877d2-120">Requirements</span></span>  
 <span data-ttu-id="877d2-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="877d2-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="877d2-122">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="877d2-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="877d2-123">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="877d2-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="877d2-124">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="877d2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="877d2-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="877d2-125">See also</span></span>

- [<span data-ttu-id="877d2-126">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="877d2-126">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="877d2-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="877d2-127">Hosting</span></span>](index.md)
