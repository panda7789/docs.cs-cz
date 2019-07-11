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
ms.openlocfilehash: d05bc472711838236ed18b00ce808d022d9581dc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758201"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="17421-102">CoUninitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="17421-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="17421-103">`CoUninitializeEE` je zastaralá a poskytuje žádné funkce.</span><span class="sxs-lookup"><span data-stu-id="17421-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17421-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17421-104">Syntax</span></span>  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="17421-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="17421-105">Remarks</span></span>  
 <span data-ttu-id="17421-106">Common language runtime prováděcí modul nemůže být uvolněna z procesu.</span><span class="sxs-lookup"><span data-stu-id="17421-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="17421-107">Vypnout volání modulu provádění [corexitprocess –](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="17421-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17421-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17421-108">See also</span></span>

- [<span data-ttu-id="17421-109">CoInitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="17421-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)
- [<span data-ttu-id="17421-110">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="17421-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
