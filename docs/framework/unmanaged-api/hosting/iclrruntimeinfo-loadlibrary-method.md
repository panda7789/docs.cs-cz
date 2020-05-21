---
title: ICLRRuntimeInfo::LoadLibrary – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadLibrary
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadLibrary
helpviewer_keywords:
- ICLRRuntimeInfo::LoadLibrary method [.NET Framework hosting]
- LoadLibrary method [.NET Framework hosting]
ms.assetid: 4517ada3-4417-4ac5-a150-73da7a87c686
topic_type:
- apiref
ms.openlocfilehash: 09c80c3a56d86943ebe00e5222bb5452ab44e150
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762172"
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="0016d-102">ICLRRuntimeInfo::LoadLibrary – metoda</span><span class="sxs-lookup"><span data-stu-id="0016d-102">ICLRRuntimeInfo::LoadLibrary Method</span></span>
<span data-ttu-id="0016d-103">Načte knihovnu .NET Framework ze společného jazykového modulu runtime (CLR) reprezentované rozhraním [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0016d-103">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="0016d-104">Tato metoda nahrazuje funkci [LoadLibraryShim –](loadlibraryshim-function.md) .</span><span class="sxs-lookup"><span data-stu-id="0016d-104">This method supersedes the [LoadLibraryShim](loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0016d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0016d-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0016d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0016d-106">Parameters</span></span>  
 `pwzDllName`  
 <span data-ttu-id="0016d-107">pro Název sestavení, které má být načteno.</span><span class="sxs-lookup"><span data-stu-id="0016d-107">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="0016d-108">mimo Popisovač načteného sestavení.</span><span class="sxs-lookup"><span data-stu-id="0016d-108">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0016d-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0016d-109">Return Value</span></span>  
 <span data-ttu-id="0016d-110">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="0016d-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0016d-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0016d-111">HRESULT</span></span>|<span data-ttu-id="0016d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0016d-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0016d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="0016d-113">S_OK</span></span>|<span data-ttu-id="0016d-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="0016d-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="0016d-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="0016d-115">E_POINTER</span></span>|<span data-ttu-id="0016d-116">`pwzDllName`nebo `phndModule` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="0016d-116">`pwzDllName` or `phndModule` is null.</span></span>|  
|<span data-ttu-id="0016d-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0016d-117">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0016d-118">Pro zpracování požadavku není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="0016d-118">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0016d-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0016d-119">Remarks</span></span>  
 <span data-ttu-id="0016d-120">Tato metoda načte pouze knihovny DLL zahrnuté do balíčku .NET Framework redistributable.</span><span class="sxs-lookup"><span data-stu-id="0016d-120">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="0016d-121">Nelze načíst uživatelsky generovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="0016d-121">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0016d-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0016d-122">Requirements</span></span>  
 <span data-ttu-id="0016d-123">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0016d-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0016d-124">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="0016d-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0016d-125">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0016d-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0016d-126">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0016d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0016d-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="0016d-127">See also</span></span>

- [<span data-ttu-id="0016d-128">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0016d-128">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="0016d-129">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="0016d-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="0016d-130">Hostování</span><span class="sxs-lookup"><span data-stu-id="0016d-130">Hosting</span></span>](index.md)
