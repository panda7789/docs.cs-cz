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
- mscorsvr.dll
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
ms.openlocfilehash: 8ddef35b1b707cc5c962402e880923dca7d4d9d6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208147"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="b67a3-102">CoEEShutDownCOM – funkce</span><span class="sxs-lookup"><span data-stu-id="b67a3-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="b67a3-103">Vynutí common language runtime (CLR) uvolnit všechny ukazatele rozhraní, které obsahuje uvnitř obálek volatelných za běhu (RCW).</span><span class="sxs-lookup"><span data-stu-id="b67a3-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="b67a3-104">To má za následek uvolnění všech RCW mezipamětí.</span><span class="sxs-lookup"><span data-stu-id="b67a3-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="b67a3-105">Tato globální funkce je zastaralá ve [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b67a3-105">This global function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="b67a3-106">Místo toho použijte vstupní bod pro konkrétní prostředí runtime.</span><span class="sxs-lookup"><span data-stu-id="b67a3-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b67a3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b67a3-107">Syntax</span></span>  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b67a3-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b67a3-108">Remarks</span></span>  
 <span data-ttu-id="b67a3-109">`CoEEShutDownCOM` Funkce nejprve uvolní všechny RCW ve všech kontextech a všechny mezipaměti a pak taky odebere všechna oznámení vše existující v instalačním programu.</span><span class="sxs-lookup"><span data-stu-id="b67a3-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="b67a3-110">Vyvolá se žádná uvolnění knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="b67a3-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="b67a3-111">Tuto funkci ovlivňuje všechny moduly runtime, která jsou načtena do procesu.</span><span class="sxs-lookup"><span data-stu-id="b67a3-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="b67a3-112">Počínaje [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], volání vstupní bod pro tuto funkci v modulu runtime specifické chcete ovlivnit.</span><span class="sxs-lookup"><span data-stu-id="b67a3-112">Beginning with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="b67a3-113">Získání vstupního bodu, zavolejte [iclrruntimeinfo::GetProcAddress –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) metodu a zadejte "Coeeshutdowncom –".</span><span class="sxs-lookup"><span data-stu-id="b67a3-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b67a3-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b67a3-114">Requirements</span></span>  
 <span data-ttu-id="b67a3-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b67a3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b67a3-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b67a3-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b67a3-117">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b67a3-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="b67a3-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b67a3-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b67a3-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b67a3-119">See also</span></span>

- [<span data-ttu-id="b67a3-120">Globální statické funkce metadat</span><span class="sxs-lookup"><span data-stu-id="b67a3-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
