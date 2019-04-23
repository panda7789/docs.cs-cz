---
title: CoUninitializeEE – funkce
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
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
ms.openlocfilehash: 7b3712b4cb66facc105a03d7bfad235f09339056
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193002"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="b698d-102">CoUninitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="b698d-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="b698d-103">`CoUninitializeEE` je zastaralá a poskytuje žádné funkce.</span><span class="sxs-lookup"><span data-stu-id="b698d-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b698d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b698d-104">Syntax</span></span>  
  
```  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="b698d-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b698d-105">Remarks</span></span>  
 <span data-ttu-id="b698d-106">Common language runtime prováděcí modul nemůže být uvolněna z procesu.</span><span class="sxs-lookup"><span data-stu-id="b698d-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="b698d-107">Vypnout volání modulu provádění [corexitprocess –](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="b698d-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b698d-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b698d-108">See also</span></span>

- [<span data-ttu-id="b698d-109">CoInitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="b698d-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)
- [<span data-ttu-id="b698d-110">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="b698d-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
