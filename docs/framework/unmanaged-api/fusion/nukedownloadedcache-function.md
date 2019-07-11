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
ms.openlocfilehash: 76ada8400573dd61c25e0dce3f49ce66b5fb30c1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773811"
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="ed95f-102">NukeDownloadedCache – funkce</span><span class="sxs-lookup"><span data-stu-id="ed95f-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="ed95f-103">Odstraní běžné mezipaměť pro stahování language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="ed95f-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed95f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed95f-104">Syntax</span></span>  
  
```cpp  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ed95f-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ed95f-105">Return Value</span></span>  
 <span data-ttu-id="ed95f-106">Tato metoda vrací standardní kódy chyb modelu COM, jak je definovaný ve WinError.h.</span><span class="sxs-lookup"><span data-stu-id="ed95f-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed95f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ed95f-107">Remarks</span></span>  
 <span data-ttu-id="ed95f-108">Mezipaměť pro stahování CLR je oblast, kde jsou uložené sestavení se silným názvem, které byly staženy z adresy URL pro opakované použití je to možné.</span><span class="sxs-lookup"><span data-stu-id="ed95f-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed95f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ed95f-109">Requirements</span></span>  
 <span data-ttu-id="ed95f-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed95f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed95f-111">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="ed95f-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ed95f-112">**Knihovna:** Soubor Fusion.dll a knihovny Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="ed95f-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="ed95f-113">Ujistěte se, že můžete cílit na správnou verzi rozhraní .NET Framework pomocí soubor Fusion.dll namísto knihovny Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="ed95f-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="ed95f-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed95f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed95f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ed95f-115">See also</span></span>

- [<span data-ttu-id="ed95f-116">CreateHistoryReader – funkce</span><span class="sxs-lookup"><span data-stu-id="ed95f-116">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [<span data-ttu-id="ed95f-117">GetHistoryFileDirectory – funkce</span><span class="sxs-lookup"><span data-stu-id="ed95f-117">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)
- [<span data-ttu-id="ed95f-118">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="ed95f-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
