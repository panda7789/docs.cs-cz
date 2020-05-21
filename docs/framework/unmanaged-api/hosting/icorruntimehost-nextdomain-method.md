---
title: ICorRuntimeHost::NextDomain – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.NextDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::NextDomain
helpviewer_keywords:
- ICorRuntimeHost::NextDomain method [.NET Framework hosting]
- NextDomain method [.NET Framework hosting]
ms.assetid: fe07a05b-f6d6-44b5-ab01-b9a6eb15c350
topic_type:
- apiref
ms.openlocfilehash: 079164d15141983711e976e0209cc22c818d9cd9
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760417"
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="72eaa-102">ICorRuntimeHost::NextDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="72eaa-102">ICorRuntimeHost::NextDomain Method</span></span>
<span data-ttu-id="72eaa-103">Získá ukazatel rozhraní do další domény ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="72eaa-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72eaa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72eaa-104">Syntax</span></span>  
  
```cpp  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72eaa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="72eaa-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="72eaa-106">pro Enumerátor získaný prostřednictvím volání [enumdomains –](icorruntimehost-enumdomains-method.md).</span><span class="sxs-lookup"><span data-stu-id="72eaa-106">[in] The enumerator that was obtained through a call to [EnumDomains](icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="72eaa-107">mimo Ukazatel rozhraní na <xref:System._AppDomain?displayProperty=nameWithType> typ, který představuje další doménu ve výčtu nebo hodnotu null, pokud žádné další domény neexistují.</span><span class="sxs-lookup"><span data-stu-id="72eaa-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72eaa-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="72eaa-108">Return Value</span></span>  
  
|<span data-ttu-id="72eaa-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="72eaa-109">HRESULT</span></span>|<span data-ttu-id="72eaa-110">Popis</span><span class="sxs-lookup"><span data-stu-id="72eaa-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="72eaa-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="72eaa-111">S_OK</span></span>|<span data-ttu-id="72eaa-112">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="72eaa-112">The operation was successful.</span></span>|  
|<span data-ttu-id="72eaa-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="72eaa-113">S_FALSE</span></span>|<span data-ttu-id="72eaa-114">Operaci se nepovedlo dokončit, nebo ve výčtu nejsou žádné další domény.</span><span class="sxs-lookup"><span data-stu-id="72eaa-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="72eaa-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="72eaa-115">E_FAIL</span></span>|<span data-ttu-id="72eaa-116">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="72eaa-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="72eaa-117">Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit.</span><span class="sxs-lookup"><span data-stu-id="72eaa-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="72eaa-118">Následná volání všech hostitelských rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="72eaa-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="72eaa-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="72eaa-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="72eaa-120">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="72eaa-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="72eaa-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72eaa-121">Requirements</span></span>  
 <span data-ttu-id="72eaa-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72eaa-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72eaa-123">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="72eaa-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="72eaa-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="72eaa-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72eaa-125">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="72eaa-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72eaa-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="72eaa-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="72eaa-127">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="72eaa-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
