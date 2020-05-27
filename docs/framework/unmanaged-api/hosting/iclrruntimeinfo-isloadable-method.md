---
title: ICLRRuntimeInfo::IsLoadable – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
ms.openlocfilehash: a1cd169fc4be5b1dd3ab1a83f4ad143ba2e2442b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007361"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="8496d-102">ICLRRuntimeInfo::IsLoadable – metoda</span><span class="sxs-lookup"><span data-stu-id="8496d-102">ICLRRuntimeInfo::IsLoadable Method</span></span>
<span data-ttu-id="8496d-103">Určuje, zda lze modul runtime spojený s tímto rozhraním načíst do aktuálního procesu, přičemž vezme v úvahu jiné moduly runtime, které mohou být do procesu již načteny.</span><span class="sxs-lookup"><span data-stu-id="8496d-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8496d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8496d-104">Syntax</span></span>  
  
```cpp  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8496d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8496d-105">Parameters</span></span>  
 `pbLoadable`  
 <span data-ttu-id="8496d-106">[out] `true` Pokud tento modul runtime může být načten do aktuálního procesu; v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="8496d-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8496d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8496d-107">Return Value</span></span>  
 <span data-ttu-id="8496d-108">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="8496d-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8496d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8496d-109">HRESULT</span></span>|<span data-ttu-id="8496d-110">Description</span><span class="sxs-lookup"><span data-stu-id="8496d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8496d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8496d-111">S_OK</span></span>|<span data-ttu-id="8496d-112">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="8496d-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="8496d-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="8496d-113">E_POINTER</span></span>|<span data-ttu-id="8496d-114">`pbLoadable`má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="8496d-114">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8496d-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8496d-115">Remarks</span></span>  
 <span data-ttu-id="8496d-116">Pokud je již do procesu načten jiný modul runtime a modul runtime přidružený k tomuto rozhraní lze načíst pro vnitroprocesové souběžné spouštění, `pbLoadable` vrátí `true` .</span><span class="sxs-lookup"><span data-stu-id="8496d-116">If another runtime is already loaded into the process, and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="8496d-117">Pokud tyto dva moduly runtime nemohou běžet souběžně v rámci procesu, `pbLoadable` vrátí `false` .</span><span class="sxs-lookup"><span data-stu-id="8496d-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="8496d-118">Například modul CLR (Common Language Runtime) verze 4 může běžet souběžně v rámci stejného procesu s CLR verze 2,0 nebo CLR verze 1,1.</span><span class="sxs-lookup"><span data-stu-id="8496d-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="8496d-119">CLR verze 1,1 a CLR verze 2,0 však nemůže spustit souběžný proces souběžného zpracování.</span><span class="sxs-lookup"><span data-stu-id="8496d-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="8496d-120">Pokud nejsou do procesu načteny žádné moduly runtime, tato metoda vždy vrátí `true` .</span><span class="sxs-lookup"><span data-stu-id="8496d-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8496d-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8496d-121">Requirements</span></span>  
 <span data-ttu-id="8496d-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8496d-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8496d-123">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="8496d-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8496d-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8496d-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8496d-125">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8496d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8496d-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="8496d-126">See also</span></span>

- [<span data-ttu-id="8496d-127">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8496d-127">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="8496d-128">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="8496d-128">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="8496d-129">Hostování</span><span class="sxs-lookup"><span data-stu-id="8496d-129">Hosting</span></span>](index.md)
