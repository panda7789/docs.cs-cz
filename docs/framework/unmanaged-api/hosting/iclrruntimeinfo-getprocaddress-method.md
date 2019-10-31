---
title: ICLRRuntimeInfo::GetProcAddress – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetProcAddress
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type:
- apiref
ms.openlocfilehash: cedda39aeebc62c6bf43f42ae2daf6f6f515fd27
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120277"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="89918-102">ICLRRuntimeInfo::GetProcAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="89918-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="89918-103">Získá adresu zadané funkce, která byla exportována z modulu CLR (Common Language Runtime) přidruženého k tomuto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="89918-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="89918-104">Tato metoda nahrazuje funkci [GetRealProcAddress –](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) .</span><span class="sxs-lookup"><span data-stu-id="89918-104">This method supersedes the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89918-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89918-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89918-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="89918-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="89918-107">pro Název exportované funkce</span><span class="sxs-lookup"><span data-stu-id="89918-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="89918-108">mimo Adresa exportované funkce</span><span class="sxs-lookup"><span data-stu-id="89918-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89918-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="89918-109">Return Value</span></span>  
 <span data-ttu-id="89918-110">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="89918-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="89918-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89918-111">HRESULT</span></span>|<span data-ttu-id="89918-112">Popis</span><span class="sxs-lookup"><span data-stu-id="89918-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="89918-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="89918-113">S_OK</span></span>|<span data-ttu-id="89918-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="89918-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="89918-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="89918-115">E_POINTER</span></span>|<span data-ttu-id="89918-116">`pszProcName` nebo `ppProc` je null.</span><span class="sxs-lookup"><span data-stu-id="89918-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="89918-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="89918-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="89918-118">Zadaná funkce není exportovanou funkcí.</span><span class="sxs-lookup"><span data-stu-id="89918-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89918-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89918-119">Remarks</span></span>  
 <span data-ttu-id="89918-120">Tato metoda způsobí, že se CLR načte, ale neinicializuje se.</span><span class="sxs-lookup"><span data-stu-id="89918-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89918-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89918-121">Requirements</span></span>  
 <span data-ttu-id="89918-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89918-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89918-123">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="89918-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="89918-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="89918-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89918-125">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89918-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89918-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89918-126">See also</span></span>

- [<span data-ttu-id="89918-127">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89918-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="89918-128">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="89918-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="89918-129">Hostování</span><span class="sxs-lookup"><span data-stu-id="89918-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
