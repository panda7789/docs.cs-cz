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
ms.openlocfilehash: 87549118742da797ef0dd1b08ae9e72c466f7841
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139575"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="a2f89-102">ICorRuntimeHost::GetConfiguration – metoda</span><span class="sxs-lookup"><span data-stu-id="a2f89-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="a2f89-103">Získává objekt, který umožňuje hostiteli určit konfiguraci zpětného volání modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="a2f89-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2f89-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2f89-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2f89-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2f89-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="a2f89-106">mimo Ukazatel na adresu objektu [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) , který lze použít ke konfiguraci CLR.</span><span class="sxs-lookup"><span data-stu-id="a2f89-106">[out] A pointer to the address of an [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2f89-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a2f89-107">Remarks</span></span>  
 <span data-ttu-id="a2f89-108">Modul CLR musí být před inicializací nakonfigurován; v opačném případě metoda `GetConfiguration` vrátí hodnotu HRESULT indikující chybu.</span><span class="sxs-lookup"><span data-stu-id="a2f89-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2f89-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a2f89-109">Requirements</span></span>  
 <span data-ttu-id="a2f89-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2f89-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2f89-111">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a2f89-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a2f89-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a2f89-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2f89-113">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="a2f89-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2f89-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a2f89-114">See also</span></span>

- [<span data-ttu-id="a2f89-115">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a2f89-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
