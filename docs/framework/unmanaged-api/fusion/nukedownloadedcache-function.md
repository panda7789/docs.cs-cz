---
title: NukeDownloadedCache – funkce
ms.date: 03/30/2017
api_name:
- NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- NukeDownloadedCache
helpviewer_keywords:
- NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0436991512713c05e60a3c10d6fbdaa17bb378c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429824"
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="45faa-102">NukeDownloadedCache – funkce</span><span class="sxs-lookup"><span data-stu-id="45faa-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="45faa-103">Odstraní běžné mezipaměť pro stahování language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="45faa-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45faa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45faa-104">Syntax</span></span>  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="45faa-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="45faa-105">Return Value</span></span>  
 <span data-ttu-id="45faa-106">Tato metoda vrátí standardní kódy chyb COM, jak jsou definovány v WinError.h.</span><span class="sxs-lookup"><span data-stu-id="45faa-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45faa-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45faa-107">Remarks</span></span>  
 <span data-ttu-id="45faa-108">Mezipaměť pro stahování CLR je oblasti, kde jsou uložené sestavení se silným názvem, které jsou staženy z adresy URL pro možné opakované použití.</span><span class="sxs-lookup"><span data-stu-id="45faa-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45faa-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="45faa-109">Requirements</span></span>  
 <span data-ttu-id="45faa-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45faa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45faa-111">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="45faa-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="45faa-112">**Knihovna:** knihovna Fusion.dll a Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="45faa-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="45faa-113">Pomocí knihovna Fusion.dll místo Mscorwks.dll zajistit, na které cílí správnou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="45faa-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="45faa-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45faa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45faa-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="45faa-115">See Also</span></span>  
 [<span data-ttu-id="45faa-116">CreateHistoryReader – funkce</span><span class="sxs-lookup"><span data-stu-id="45faa-116">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [<span data-ttu-id="45faa-117">GetHistoryFileDirectory – funkce</span><span class="sxs-lookup"><span data-stu-id="45faa-117">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 [<span data-ttu-id="45faa-118">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="45faa-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
