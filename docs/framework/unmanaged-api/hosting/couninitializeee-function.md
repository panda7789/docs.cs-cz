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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985735"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="1c588-102">CoUninitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="1c588-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="1c588-103">`CoUninitializeEE` je zastaralá a poskytuje žádné funkce.</span><span class="sxs-lookup"><span data-stu-id="1c588-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c588-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c588-104">Syntax</span></span>  
  
```  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="1c588-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c588-105">Remarks</span></span>  
 <span data-ttu-id="1c588-106">Common language runtime prováděcí modul nemůže být uvolněna z procesu.</span><span class="sxs-lookup"><span data-stu-id="1c588-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="1c588-107">Vypnout volání modulu provádění [corexitprocess –](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="1c588-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c588-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c588-108">See also</span></span>

- [<span data-ttu-id="1c588-109">CoInitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="1c588-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)
- [<span data-ttu-id="1c588-110">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="1c588-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
