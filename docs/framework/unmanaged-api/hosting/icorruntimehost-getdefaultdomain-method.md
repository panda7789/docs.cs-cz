---
title: ICorRuntimeHost::GetDefaultDomain – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetDefaultDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type:
- apiref
ms.openlocfilehash: a23083777d0cd5965511f3689578a60220008420
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762227"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="5aa30-102">ICorRuntimeHost::GetDefaultDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="5aa30-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="5aa30-103">Načte ukazatel rozhraní typu <xref:System._AppDomain?displayProperty=nameWithType> , který představuje výchozí doménu pro aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="5aa30-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5aa30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5aa30-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5aa30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5aa30-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="5aa30-106">mimo Ukazatel rozhraní typu <xref:System._AppDomain?displayProperty=nameWithType> na <xref:System.AppDomain> instanci, která představuje výchozí doménu aplikace pro daný proces.</span><span class="sxs-lookup"><span data-stu-id="5aa30-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="5aa30-107">Tento ukazatel je typu `IUnknown` , takže volající by obecně volali, `QueryInterface` aby získal ukazatel rozhraní typu <xref:System._AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5aa30-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5aa30-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5aa30-108">Return Value</span></span>  
  
|<span data-ttu-id="5aa30-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5aa30-109">HRESULT</span></span>|<span data-ttu-id="5aa30-110">Popis</span><span class="sxs-lookup"><span data-stu-id="5aa30-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5aa30-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5aa30-111">S_OK</span></span>|<span data-ttu-id="5aa30-112">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="5aa30-112">The operation was successful.</span></span>|  
|<span data-ttu-id="5aa30-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="5aa30-113">S_FALSE</span></span>|<span data-ttu-id="5aa30-114">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="5aa30-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="5aa30-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5aa30-115">E_FAIL</span></span>|<span data-ttu-id="5aa30-116">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="5aa30-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="5aa30-117">Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit.</span><span class="sxs-lookup"><span data-stu-id="5aa30-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="5aa30-118">Následná volání všech hostitelských rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5aa30-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5aa30-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5aa30-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5aa30-120">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="5aa30-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5aa30-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5aa30-121">Requirements</span></span>  
 <span data-ttu-id="5aa30-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5aa30-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5aa30-123">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5aa30-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5aa30-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5aa30-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5aa30-125">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="5aa30-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aa30-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="5aa30-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="5aa30-127">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5aa30-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
