---
title: CoUninitializeCor – funkce
ms.date: 03/30/2017
api_name:
- CoUninitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeCor
helpviewer_keywords:
- CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type:
- apiref
ms.openlocfilehash: 8a8c2764398d737192190f91646d45f4edf3a0e4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616475"
---
# <a name="couninitializecor-function"></a><span data-ttu-id="347f9-102">CoUninitializeCor – funkce</span><span class="sxs-lookup"><span data-stu-id="347f9-102">CoUninitializeCor Function</span></span>
<span data-ttu-id="347f9-103">`CoUninitializeCor`je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="347f9-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="347f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="347f9-104">Syntax</span></span>  
  
```cpp  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="347f9-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="347f9-105">Remarks</span></span>  
 <span data-ttu-id="347f9-106">Modul CLR (Common Language Runtime) nelze uvolnit z procesu.</span><span class="sxs-lookup"><span data-stu-id="347f9-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="347f9-107">Chcete-li modul runtime zcela odebrat ze spuštěného procesu, je nutné tento proces vypnout.</span><span class="sxs-lookup"><span data-stu-id="347f9-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="347f9-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="347f9-108">See also</span></span>

- [<span data-ttu-id="347f9-109">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="347f9-109">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
