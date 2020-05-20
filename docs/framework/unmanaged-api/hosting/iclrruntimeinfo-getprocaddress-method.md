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
ms.openlocfilehash: 2690a5c2e7c499d68ef9e903c62bff8f85e72e8e
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703864"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="9872b-102">ICLRRuntimeInfo::GetProcAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="9872b-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="9872b-103">Získá adresu zadané funkce, která byla exportována z modulu CLR (Common Language Runtime) přidruženého k tomuto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9872b-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="9872b-104">Tato metoda nahrazuje funkci [GetRealProcAddress –](getrealprocaddress-function.md) .</span><span class="sxs-lookup"><span data-stu-id="9872b-104">This method supersedes the [GetRealProcAddress](getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9872b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9872b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9872b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9872b-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="9872b-107">pro Název exportované funkce</span><span class="sxs-lookup"><span data-stu-id="9872b-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="9872b-108">mimo Adresa exportované funkce</span><span class="sxs-lookup"><span data-stu-id="9872b-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9872b-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9872b-109">Return Value</span></span>  
 <span data-ttu-id="9872b-110">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="9872b-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9872b-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9872b-111">HRESULT</span></span>|<span data-ttu-id="9872b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9872b-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9872b-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="9872b-113">S_OK</span></span>|<span data-ttu-id="9872b-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="9872b-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="9872b-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="9872b-115">E_POINTER</span></span>|<span data-ttu-id="9872b-116">`pszProcName`nebo `ppProc` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="9872b-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="9872b-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="9872b-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="9872b-118">Zadaná funkce není exportovanou funkcí.</span><span class="sxs-lookup"><span data-stu-id="9872b-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9872b-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9872b-119">Remarks</span></span>  
 <span data-ttu-id="9872b-120">Tato metoda způsobí, že se CLR načte, ale neinicializuje se.</span><span class="sxs-lookup"><span data-stu-id="9872b-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9872b-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9872b-121">Requirements</span></span>  
 <span data-ttu-id="9872b-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9872b-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9872b-123">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="9872b-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9872b-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9872b-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9872b-125">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9872b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9872b-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="9872b-126">See also</span></span>

- [<span data-ttu-id="9872b-127">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9872b-127">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="9872b-128">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="9872b-128">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="9872b-129">Hostování</span><span class="sxs-lookup"><span data-stu-id="9872b-129">Hosting</span></span>](index.md)
