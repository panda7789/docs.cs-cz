---
title: CoEEShutDownCOM – funkce
ms.date: 03/30/2017
api_name:
- CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CoEEShutDownCOM
helpviewer_keywords:
- CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0b30cc2c499644ffc97a734e1554e4e352b34af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431887"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="c8c2e-102">CoEEShutDownCOM – funkce</span><span class="sxs-lookup"><span data-stu-id="c8c2e-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="c8c2e-103">Vynutí modul CLR (CLR) Chcete-li uvolnit všechny ukazatele rozhraní, které uchovává uvnitř běhové obálky s možností (RCW).</span><span class="sxs-lookup"><span data-stu-id="c8c2e-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="c8c2e-104">To má za následek uvolnění všech RCW mezipamětí.</span><span class="sxs-lookup"><span data-stu-id="c8c2e-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="c8c2e-105">Globální funkce je ve zastaralá [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8c2e-105">This global function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="c8c2e-106">Místo toho použijte vstupní bod pro konkrétní modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="c8c2e-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8c2e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8c2e-107">Syntax</span></span>  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c8c2e-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c8c2e-108">Remarks</span></span>  
 <span data-ttu-id="c8c2e-109">`CoEEShutDownCOM` Funkce nejprve uvolní všechny RCWs v všechny kontexty a všechny mezipaměti a pak odebere všechna oznámení rozbalovací úplné stávající v instalačním programu.</span><span class="sxs-lookup"><span data-stu-id="c8c2e-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="c8c2e-110">Dojde k žádné uvolnění knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="c8c2e-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="c8c2e-111">Tato funkce ovlivňuje všechny moduly runtime, která jsou načtena do procesu.</span><span class="sxs-lookup"><span data-stu-id="c8c2e-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="c8c2e-112">Od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], volání vstupní bod pro tuto funkci na konkrétní runtime chcete ovlivnit.</span><span class="sxs-lookup"><span data-stu-id="c8c2e-112">Beginning with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="c8c2e-113">Chcete-li získat vstupního bodu, zavolejte [iclrruntimeinfo::GetProcAddress –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) metoda a zadejte "Coeeshutdowncom –".</span><span class="sxs-lookup"><span data-stu-id="c8c2e-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8c2e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8c2e-114">Requirements</span></span>  
 <span data-ttu-id="c8c2e-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8c2e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8c2e-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c8c2e-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c8c2e-117">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c8c2e-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c8c2e-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8c2e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8c2e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8c2e-119">See Also</span></span>  
 [<span data-ttu-id="c8c2e-120">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="c8c2e-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
