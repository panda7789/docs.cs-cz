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
ms.openlocfilehash: 3eb8bffee9d30a89c39a900e600ebf171456b9f3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616785"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="b69f7-102">CoEEShutDownCOM – funkce</span><span class="sxs-lookup"><span data-stu-id="b69f7-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="b69f7-103">Vynutí modul CLR (Common Language Runtime), aby uvolnil všechny ukazatele rozhraní, které se nachází uvnitř za běhu volat obálky (RCW).</span><span class="sxs-lookup"><span data-stu-id="b69f7-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="b69f7-104">To má vliv na uvolnění všech mezipamětí RCW cache.</span><span class="sxs-lookup"><span data-stu-id="b69f7-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="b69f7-105">Tato globální funkce je zastaralá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b69f7-105">This global function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="b69f7-106">Místo toho použijte vstupní bod konkrétního modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b69f7-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b69f7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b69f7-107">Syntax</span></span>  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b69f7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b69f7-108">Remarks</span></span>  
 <span data-ttu-id="b69f7-109">`CoEEShutDownCOM`Funkce nejprve uvolní všechny RCW ve všech kontextech a ve všech mezipamětích a následně odebere všechna oznámení, která jsou v instalaci existující.</span><span class="sxs-lookup"><span data-stu-id="b69f7-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="b69f7-110">Nedochází k uvolnění knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="b69f7-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="b69f7-111">Tato funkce má vliv na všechny moduly runtime, které jsou načteny do procesu.</span><span class="sxs-lookup"><span data-stu-id="b69f7-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="b69f7-112">Počínaje .NET Framework 4 volejte vstupní bod pro tuto funkci pro konkrétní modul runtime, který chcete ovlivnit.</span><span class="sxs-lookup"><span data-stu-id="b69f7-112">Beginning with the .NET Framework 4, call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="b69f7-113">Chcete-li získat vstupní bod, zavolejte metodu [ICLRRuntimeInfo:: GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) a zadejte "CoEEShutDownCOM –".</span><span class="sxs-lookup"><span data-stu-id="b69f7-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b69f7-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b69f7-114">Requirements</span></span>  
 <span data-ttu-id="b69f7-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b69f7-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b69f7-116">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b69f7-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b69f7-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b69f7-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b69f7-118">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b69f7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b69f7-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b69f7-119">See also</span></span>

- [<span data-ttu-id="b69f7-120">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="b69f7-120">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
