---
title: "ICorRuntimeHost::GetConfiguration – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.GetConfiguration
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 446142d8bd61d384c3b8a58d5469e27a7a512c60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="86c9d-102">ICorRuntimeHost::GetConfiguration – metoda</span><span class="sxs-lookup"><span data-stu-id="86c9d-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="86c9d-103">Získá objekt, který umožňuje na hostiteli a poté zadejte konfiguraci zpětného volání common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="86c9d-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86c9d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86c9d-104">Syntax</span></span>  
  
```  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86c9d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86c9d-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="86c9d-106">[out] Ukazatel na adresu [icorconfiguration –](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) objekt, který můžete použít ke konfiguraci modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="86c9d-106">[out] A pointer to the address of an [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86c9d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="86c9d-107">Remarks</span></span>  
 <span data-ttu-id="86c9d-108">Modul CLR musí být nakonfigurovaná před jeho inicializace; jinak `GetConfiguration` metoda vrátí HRESULT indikující chybu.</span><span class="sxs-lookup"><span data-stu-id="86c9d-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86c9d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="86c9d-109">Requirements</span></span>  
 <span data-ttu-id="86c9d-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86c9d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86c9d-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="86c9d-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="86c9d-112">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="86c9d-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86c9d-113">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="86c9d-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c9d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="86c9d-114">See Also</span></span>  
 [<span data-ttu-id="86c9d-115">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="86c9d-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
