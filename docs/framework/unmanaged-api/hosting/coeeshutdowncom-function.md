---
title: "CoEEShutDownCOM – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CoEEShutDownCOM
helpviewer_keywords: CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ae339310c2bfd186cae798ff603d69735abeefd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="19bcc-102">CoEEShutDownCOM – funkce</span><span class="sxs-lookup"><span data-stu-id="19bcc-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="19bcc-103">Vynutí modul CLR (CLR) Chcete-li uvolnit všechny ukazatele rozhraní, které uchovává uvnitř běhové obálky s možností (RCW).</span><span class="sxs-lookup"><span data-stu-id="19bcc-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="19bcc-104">To má za následek uvolnění všech RCW mezipamětí.</span><span class="sxs-lookup"><span data-stu-id="19bcc-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="19bcc-105">Globální funkce je ve zastaralá [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="19bcc-105">This global function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="19bcc-106">Místo toho použijte vstupní bod pro konkrétní modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="19bcc-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19bcc-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19bcc-107">Syntax</span></span>  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="19bcc-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19bcc-108">Remarks</span></span>  
 <span data-ttu-id="19bcc-109">`CoEEShutDownCOM` Funkce nejprve uvolní všechny RCWs v všechny kontexty a všechny mezipaměti a pak odebere všechna oznámení rozbalovací úplné stávající v instalačním programu.</span><span class="sxs-lookup"><span data-stu-id="19bcc-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="19bcc-110">Dojde k žádné uvolnění knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="19bcc-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="19bcc-111">Tato funkce ovlivňuje všechny moduly runtime, která jsou načtena do procesu.</span><span class="sxs-lookup"><span data-stu-id="19bcc-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="19bcc-112">Od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], volání vstupní bod pro tuto funkci na konkrétní runtime chcete ovlivnit.</span><span class="sxs-lookup"><span data-stu-id="19bcc-112">Beginning with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="19bcc-113">Chcete-li získat vstupního bodu, zavolejte [iclrruntimeinfo::GetProcAddress –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) metoda a zadejte "Coeeshutdowncom –".</span><span class="sxs-lookup"><span data-stu-id="19bcc-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19bcc-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="19bcc-114">Requirements</span></span>  
 <span data-ttu-id="19bcc-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19bcc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19bcc-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="19bcc-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="19bcc-117">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="19bcc-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="19bcc-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19bcc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19bcc-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="19bcc-119">See Also</span></span>  
 [<span data-ttu-id="19bcc-120">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="19bcc-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
