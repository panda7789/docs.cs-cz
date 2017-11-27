---
title: "NukeDownloadedCache – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: NukeDownloadedCache
helpviewer_keywords: NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5ff24cf46ab24fe94ab19cee04d9e32ed1a34b53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="ff8af-102">NukeDownloadedCache – funkce</span><span class="sxs-lookup"><span data-stu-id="ff8af-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="ff8af-103">Odstraní běžné mezipaměť pro stahování language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="ff8af-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff8af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff8af-104">Syntax</span></span>  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ff8af-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ff8af-105">Return Value</span></span>  
 <span data-ttu-id="ff8af-106">Tato metoda vrátí standardní kódy chyb COM, jak jsou definovány v WinError.h.</span><span class="sxs-lookup"><span data-stu-id="ff8af-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff8af-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff8af-107">Remarks</span></span>  
 <span data-ttu-id="ff8af-108">Mezipaměť pro stahování CLR je oblasti, kde jsou uložené sestavení se silným názvem, které jsou staženy z adresy URL pro možné opakované použití.</span><span class="sxs-lookup"><span data-stu-id="ff8af-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff8af-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff8af-109">Requirements</span></span>  
 <span data-ttu-id="ff8af-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff8af-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff8af-111">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="ff8af-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ff8af-112">**Knihovna:** knihovna Fusion.dll a Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="ff8af-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="ff8af-113">Pomocí knihovna Fusion.dll místo Mscorwks.dll zajistit, na které cílí správnou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ff8af-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="ff8af-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff8af-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff8af-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff8af-115">See Also</span></span>  
 [<span data-ttu-id="ff8af-116">Createhistoryreader – funkce</span><span class="sxs-lookup"><span data-stu-id="ff8af-116">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [<span data-ttu-id="ff8af-117">Gethistoryfiledirectory – funkce</span><span class="sxs-lookup"><span data-stu-id="ff8af-117">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 [<span data-ttu-id="ff8af-118">Fúze globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="ff8af-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
