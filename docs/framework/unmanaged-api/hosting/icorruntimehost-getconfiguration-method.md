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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf74da6eb0e7ce0215023a9a58d6b88c57c4fe8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936939"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="b1df4-102">ICorRuntimeHost::GetConfiguration – metoda</span><span class="sxs-lookup"><span data-stu-id="b1df4-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="b1df4-103">Získá objekt, který umožňuje hostiteli zadejte požadovanou konfiguraci zpětného volání modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="b1df4-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1df4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1df4-104">Syntax</span></span>  
  
```  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1df4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1df4-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="b1df4-106">[out] Ukazatel na adresu [icorconfiguration –](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) objekt, který můžete použít ke konfiguraci modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="b1df4-106">[out] A pointer to the address of an [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1df4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1df4-107">Remarks</span></span>  
 <span data-ttu-id="b1df4-108">Modul CLR musí být nakonfigurované před jeho inicializaci; v opačném případě `GetConfiguration` metoda vrátí hodnotu udávající chybu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="b1df4-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1df4-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1df4-109">Requirements</span></span>  
 <span data-ttu-id="b1df4-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1df4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1df4-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b1df4-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1df4-112">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b1df4-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1df4-113">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="b1df4-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1df4-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1df4-114">See also</span></span>

- [<span data-ttu-id="b1df4-115">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b1df4-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
