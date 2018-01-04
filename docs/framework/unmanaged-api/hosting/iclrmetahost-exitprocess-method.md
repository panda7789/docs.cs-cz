---
title: "ICLRMetaHost::ExitProcess – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.ExitProcess
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2407dd8fb4911bd7e6d46c973ebbab836da4f8fa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="0bc2f-102">ICLRMetaHost::ExitProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="0bc2f-102">ICLRMetaHost::ExitProcess Method</span></span>
<span data-ttu-id="0bc2f-103">Pokusí se korektně vypnout všechny načíst moduly runtime a pak ukončit proces.</span><span class="sxs-lookup"><span data-stu-id="0bc2f-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="0bc2f-104">Nahrazuje [corexitprocess –](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="0bc2f-104">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bc2f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bc2f-105">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0bc2f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0bc2f-106">Parameters</span></span>  
 `iExitCode`  
 <span data-ttu-id="0bc2f-107">[v] Kód ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="0bc2f-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0bc2f-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0bc2f-108">Return Value</span></span>  
 <span data-ttu-id="0bc2f-109">Tato metoda nikdy vrátí, takže jeho návratová hodnota není definován.</span><span class="sxs-lookup"><span data-stu-id="0bc2f-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bc2f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0bc2f-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bc2f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0bc2f-111">Requirements</span></span>  
 <span data-ttu-id="0bc2f-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bc2f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bc2f-113">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="0bc2f-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0bc2f-114">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0bc2f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0bc2f-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bc2f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bc2f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="0bc2f-116">See Also</span></span>  
 [<span data-ttu-id="0bc2f-117">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0bc2f-117">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="0bc2f-118">Hostování</span><span class="sxs-lookup"><span data-stu-id="0bc2f-118">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
