---
title: "CoUninitializeEE – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoUninitializeEE
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CoUninitializeEE
helpviewer_keywords: CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d64064c29d2a03578305f71a37e759907814727e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="couninitializeee-function"></a><span data-ttu-id="f337d-102">CoUninitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="f337d-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="f337d-103">`CoUninitializeEE`je zastaralá a poskytuje žádné funkce.</span><span class="sxs-lookup"><span data-stu-id="f337d-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f337d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f337d-104">Syntax</span></span>  
  
```  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="f337d-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f337d-105">Remarks</span></span>  
 <span data-ttu-id="f337d-106">Modul provádění běžných runtime jazyka nemůže být uvolněna z procesu.</span><span class="sxs-lookup"><span data-stu-id="f337d-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="f337d-107">Vypnout hovoru stroj provádění [corexitprocess –](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="f337d-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f337d-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="f337d-108">See Also</span></span>  
 [<span data-ttu-id="f337d-109">Coinitializeee – funkce</span><span class="sxs-lookup"><span data-stu-id="f337d-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 [<span data-ttu-id="f337d-110">Globální statické funkce metadat</span><span class="sxs-lookup"><span data-stu-id="f337d-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
