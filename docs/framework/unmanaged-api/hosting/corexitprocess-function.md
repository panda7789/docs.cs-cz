---
title: "CorExitProcess – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CorExitProcess
helpviewer_keywords: CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75b35631bad5de46d48ed818c6f929f25a5f7e66
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="corexitprocess-function"></a><span data-ttu-id="3d2d1-102">CorExitProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="3d2d1-102">CorExitProcess Function</span></span>
<span data-ttu-id="3d2d1-103">Ukončí proces aktuální nespravované.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="3d2d1-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3d2d1-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="3d2d1-105">Použití [iclrmetahost::exitprocess –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d2d1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d2d1-106">Syntax</span></span>  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d2d1-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="3d2d1-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="3d2d1-108">Celé číslo, které určuje kód ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d2d1-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d2d1-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d2d1-110">Od verze [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` ukončí všechny Začínáme runtime v procesu, ne jenom modul runtime, ke kterému bylo svázáno starší verze rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-110">Beginning with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d2d1-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3d2d1-111">Requirements</span></span>  
 <span data-ttu-id="3d2d1-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d2d1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d2d1-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3d2d1-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3d2d1-114">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3d2d1-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d2d1-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d2d1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d2d1-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d2d1-116">See Also</span></span>  
 [<span data-ttu-id="3d2d1-117">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="3d2d1-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
