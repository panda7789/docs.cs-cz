---
title: ICorRuntimeHost::GetConfiguration – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type:
- apiref
ms.openlocfilehash: 88abdbc62c8b27f48c5629afb99ab6e30ee67e00
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762263"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="1876d-102">ICorRuntimeHost::GetConfiguration – metoda</span><span class="sxs-lookup"><span data-stu-id="1876d-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="1876d-103">Získává objekt, který umožňuje hostiteli určit konfiguraci zpětného volání modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="1876d-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1876d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1876d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1876d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1876d-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="1876d-106">mimo Ukazatel na adresu objektu [ICorConfiguration](icorconfiguration-interface.md) , který lze použít ke konfiguraci CLR.</span><span class="sxs-lookup"><span data-stu-id="1876d-106">[out] A pointer to the address of an [ICorConfiguration](icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1876d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1876d-107">Remarks</span></span>  
 <span data-ttu-id="1876d-108">Modul CLR musí být před inicializací nakonfigurován; v opačném případě `GetConfiguration` Metoda vrátí hodnotu HRESULT indikující chybu.</span><span class="sxs-lookup"><span data-stu-id="1876d-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1876d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1876d-109">Requirements</span></span>  
 <span data-ttu-id="1876d-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1876d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1876d-111">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1876d-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1876d-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1876d-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1876d-113">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="1876d-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1876d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="1876d-114">See also</span></span>

- [<span data-ttu-id="1876d-115">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1876d-115">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
