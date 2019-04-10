---
title: ICLRMetaHost::ExitProcess – metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.ExitProcess
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64c212d064ad658678926690d1e680afe27c7c99
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219236"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="9636a-102">ICLRMetaHost::ExitProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="9636a-102">ICLRMetaHost::ExitProcess Method</span></span>
<span data-ttu-id="9636a-103">Pokusí se korektně vypnout všechny načtené moduly runtime a poté ukončí proces.</span><span class="sxs-lookup"><span data-stu-id="9636a-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="9636a-104">Nahrazuje [corexitprocess –](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="9636a-104">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9636a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9636a-105">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9636a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9636a-106">Parameters</span></span>  
 `iExitCode`  
 <span data-ttu-id="9636a-107">[in] Ukončovací kód procesu.</span><span class="sxs-lookup"><span data-stu-id="9636a-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9636a-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9636a-108">Return Value</span></span>  
 <span data-ttu-id="9636a-109">Tato metoda nikdy nevrátí, tak její návratová hodnota není definována.</span><span class="sxs-lookup"><span data-stu-id="9636a-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9636a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9636a-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9636a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9636a-111">Requirements</span></span>  
 <span data-ttu-id="9636a-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9636a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9636a-113">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9636a-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9636a-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9636a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9636a-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9636a-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9636a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9636a-116">See also</span></span>

- [<span data-ttu-id="9636a-117">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9636a-117">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="9636a-118">Hostování</span><span class="sxs-lookup"><span data-stu-id="9636a-118">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
