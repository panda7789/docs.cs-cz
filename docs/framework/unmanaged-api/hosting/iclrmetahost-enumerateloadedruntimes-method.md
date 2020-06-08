---
title: ICLRMetaHost::EnumerateLoadedRuntimes – metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
ms.openlocfilehash: 7b09bb9c3abcb23997bfd412c3ea939404e583c1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504170"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="c244e-102">ICLRMetaHost::EnumerateLoadedRuntimes – metoda</span><span class="sxs-lookup"><span data-stu-id="c244e-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="c244e-103">Vrátí výčet, který obsahuje platný ukazatel rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) pro každou verzi modulu CLR (Common Language Runtime), který je načten v daném procesu.</span><span class="sxs-lookup"><span data-stu-id="c244e-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="c244e-104">Tato metoda nahrazuje funkci [GetVersionFromProcess –](getversionfromprocess-function.md) .</span><span class="sxs-lookup"><span data-stu-id="c244e-104">This method supersedes the [GetVersionFromProcess](getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c244e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c244e-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c244e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c244e-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="c244e-107">pro Popisovač procesu pro kontrolu načtených modulů runtime.</span><span class="sxs-lookup"><span data-stu-id="c244e-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="c244e-108">mimo <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>Výčet rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) odpovídajících každému CLR, který je načten procesem.</span><span class="sxs-lookup"><span data-stu-id="c244e-108">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c244e-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c244e-109">Return Value</span></span>  
 <span data-ttu-id="c244e-110">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="c244e-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c244e-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c244e-111">HRESULT</span></span>|<span data-ttu-id="c244e-112">Description</span><span class="sxs-lookup"><span data-stu-id="c244e-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c244e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="c244e-113">S_OK</span></span>|<span data-ttu-id="c244e-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="c244e-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="c244e-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="c244e-115">E_POINTER</span></span>|<span data-ttu-id="c244e-116">`ppEnumerator`má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c244e-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c244e-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c244e-117">Remarks</span></span>  
 <span data-ttu-id="c244e-118">Tato metoda uvádí všechny načtené moduly runtime, i když byly načteny pomocí zastaralých funkcí, jako je [CorBindToRuntime](corbindtoruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="c244e-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c244e-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c244e-119">Requirements</span></span>  
 <span data-ttu-id="c244e-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c244e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c244e-121">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="c244e-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c244e-122">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c244e-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c244e-123">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c244e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c244e-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c244e-124">See also</span></span>

- [<span data-ttu-id="c244e-125">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c244e-125">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="c244e-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="c244e-126">Hosting</span></span>](index.md)
