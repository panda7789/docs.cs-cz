---
title: ICorRuntimeHost::CreateDomain – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type:
- apiref
ms.openlocfilehash: 74f17c77e74edb1226dda2d9ebaa9486e1769ce4
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762354"
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="1c5cb-102">ICorRuntimeHost::CreateDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="1c5cb-102">ICorRuntimeHost::CreateDomain Method</span></span>
<span data-ttu-id="1c5cb-103">Vytvoří doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="1c5cb-103">Creates an application domain.</span></span> <span data-ttu-id="1c5cb-104">Volající obdrží ukazatel rozhraní typu <xref:System._AppDomain> na instanci typu <xref:System.AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1c5cb-104">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c5cb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c5cb-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c5cb-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c5cb-106">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="1c5cb-107">pro Volitelný parametr, který slouží k poskytnutí popisného názvu doméně.</span><span class="sxs-lookup"><span data-stu-id="1c5cb-107">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="1c5cb-108">Tento popisný název lze zobrazit v uživatelských rozhraních, jako jsou například ladicí programy, a identifikovat doménu.</span><span class="sxs-lookup"><span data-stu-id="1c5cb-108">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="1c5cb-109">pro Volitelné pole ukazatelů na `IIdentity` instance, které reprezentují legitimace namapované prostřednictvím zásad zabezpečení, aby bylo možné vytvořit sadu oprávnění.</span><span class="sxs-lookup"><span data-stu-id="1c5cb-109">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="1c5cb-110">`IIdentity`Objekt lze získat voláním metody [createevidence –](icorruntimehost-createevidence-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1c5cb-110">An `IIdentity` object can be obtained by calling the [CreateEvidence](icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="1c5cb-111">mimo Ukazatel rozhraní typu <xref:System._AppDomain> na instanci <xref:System.AppDomain?displayProperty=nameWithType> , která může být použita k další kontrole domény.</span><span class="sxs-lookup"><span data-stu-id="1c5cb-111">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c5cb-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1c5cb-112">Return Value</span></span>  
  
|<span data-ttu-id="1c5cb-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1c5cb-113">HRESULT</span></span>|<span data-ttu-id="1c5cb-114">Popis</span><span class="sxs-lookup"><span data-stu-id="1c5cb-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1c5cb-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="1c5cb-115">S_OK</span></span>|<span data-ttu-id="1c5cb-116">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="1c5cb-116">The operation was successful.</span></span>|  
|<span data-ttu-id="1c5cb-117">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1c5cb-117">S_FALSE</span></span>|<span data-ttu-id="1c5cb-118">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="1c5cb-118">The operation failed to complete.</span></span>|  
|<span data-ttu-id="1c5cb-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1c5cb-119">E_FAIL</span></span>|<span data-ttu-id="1c5cb-120">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="1c5cb-120">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="1c5cb-121">Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit.</span><span class="sxs-lookup"><span data-stu-id="1c5cb-121">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="1c5cb-122">Následná volání všech hostitelských rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1c5cb-122">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1c5cb-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1c5cb-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1c5cb-124">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="1c5cb-124">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1c5cb-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1c5cb-125">Requirements</span></span>  
 <span data-ttu-id="1c5cb-126">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c5cb-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c5cb-127">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1c5cb-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1c5cb-128">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1c5cb-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1c5cb-129">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="1c5cb-129">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c5cb-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c5cb-130">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="1c5cb-131">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1c5cb-131">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
