---
title: CoUninitializeEE – funkce
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeEE
helpviewer_keywords:
- CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73fa281d28e9b5362ff386b55b07dd431f1915f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429179"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="d53b9-102">CoUninitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="d53b9-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="d53b9-103">`CoUninitializeEE` je zastaralá a poskytuje žádné funkce.</span><span class="sxs-lookup"><span data-stu-id="d53b9-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d53b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d53b9-104">Syntax</span></span>  
  
```  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="d53b9-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d53b9-105">Remarks</span></span>  
 <span data-ttu-id="d53b9-106">Modul provádění běžných runtime jazyka nemůže být uvolněna z procesu.</span><span class="sxs-lookup"><span data-stu-id="d53b9-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="d53b9-107">Vypnout hovoru stroj provádění [corexitprocess –](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="d53b9-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d53b9-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="d53b9-108">See Also</span></span>  
 [<span data-ttu-id="d53b9-109">CoInitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="d53b9-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 [<span data-ttu-id="d53b9-110">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="d53b9-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
