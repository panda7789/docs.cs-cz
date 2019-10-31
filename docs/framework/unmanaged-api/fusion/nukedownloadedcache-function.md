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
ms.openlocfilehash: 8f97614412eb2d49b202e86bdabc727159deb5d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131688"
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="dcf93-102">NukeDownloadedCache – funkce</span><span class="sxs-lookup"><span data-stu-id="dcf93-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="dcf93-103">Odstraní mezipaměť pro stažení modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="dcf93-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcf93-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcf93-104">Syntax</span></span>  
  
```cpp  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="dcf93-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dcf93-105">Return Value</span></span>  
 <span data-ttu-id="dcf93-106">Tato metoda vrátí standardní chybové kódy modelu COM, jak je definováno v WinError. h.</span><span class="sxs-lookup"><span data-stu-id="dcf93-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcf93-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dcf93-107">Remarks</span></span>  
 <span data-ttu-id="dcf93-108">Mezipaměť pro stažení CLR je oblast, kde jsou uložena sestavení se silným názvem, která jsou stažena z adresy URL pro možné opakované použití.</span><span class="sxs-lookup"><span data-stu-id="dcf93-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcf93-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dcf93-109">Requirements</span></span>  
 <span data-ttu-id="dcf93-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcf93-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcf93-111">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="dcf93-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="dcf93-112">**Knihovna:** Fusion. dll a knihovny Mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="dcf93-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="dcf93-113">Použijte knihovnu Fusion. dll namísto knihovny Mscorwks. dll, abyste se ujistili, že cílíte na správnou verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dcf93-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="dcf93-114">**Verze .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcf93-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcf93-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dcf93-115">See also</span></span>

- [<span data-ttu-id="dcf93-116">CreateHistoryReader – funkce</span><span class="sxs-lookup"><span data-stu-id="dcf93-116">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="dcf93-117">GetHistoryFileDirectory – funkce</span><span class="sxs-lookup"><span data-stu-id="dcf93-117">GetHistoryFileDirectory Function</span></span>](gethistoryfiledirectory-function.md)
- [<span data-ttu-id="dcf93-118">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="dcf93-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
