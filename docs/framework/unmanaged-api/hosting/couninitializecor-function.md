---
title: CoUninitializeCor – funkce
ms.date: 03/30/2017
api_name:
- CoUninitializeCor
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeCor
helpviewer_keywords:
- CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 305a8d7b5a800c46ed814b1e654947859dc9bd03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427808"
---
# <a name="couninitializecor-function"></a><span data-ttu-id="cd876-102">CoUninitializeCor – funkce</span><span class="sxs-lookup"><span data-stu-id="cd876-102">CoUninitializeCor Function</span></span>
<span data-ttu-id="cd876-103">`CoUninitializeCor` je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="cd876-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd876-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd876-104">Syntax</span></span>  
  
```  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="cd876-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd876-105">Remarks</span></span>  
 <span data-ttu-id="cd876-106">Modul common language runtime nemůže být uvolněna z procesu.</span><span class="sxs-lookup"><span data-stu-id="cd876-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="cd876-107">Modul runtime úplně odebrat ze spuštěných procesů, je nutné vypnout tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="cd876-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd876-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd876-108">See Also</span></span>  
 [<span data-ttu-id="cd876-109">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="cd876-109">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
