---
title: "CoUninitializeCor – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoUninitializeCor
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CoUninitializeCor
helpviewer_keywords: CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 57740ed8f20891b240bca5e9e19591484022b8ec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="couninitializecor-function"></a><span data-ttu-id="ce09f-102">CoUninitializeCor – funkce</span><span class="sxs-lookup"><span data-stu-id="ce09f-102">CoUninitializeCor Function</span></span>
<span data-ttu-id="ce09f-103">`CoUninitializeCor`je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="ce09f-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce09f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce09f-104">Syntax</span></span>  
  
```  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="ce09f-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce09f-105">Remarks</span></span>  
 <span data-ttu-id="ce09f-106">Modul common language runtime nemůže být uvolněna z procesu.</span><span class="sxs-lookup"><span data-stu-id="ce09f-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="ce09f-107">Modul runtime úplně odebrat ze spuštěných procesů, je nutné vypnout tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="ce09f-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce09f-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce09f-108">See Also</span></span>  
 [<span data-ttu-id="ce09f-109">Globální statické funkce metadat</span><span class="sxs-lookup"><span data-stu-id="ce09f-109">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
