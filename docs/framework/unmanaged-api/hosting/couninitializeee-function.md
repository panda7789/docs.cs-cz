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
ms.openlocfilehash: 3531cfc0815c3f8a9479e35b2df60b2825801b39
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136854"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="eb7e1-102">CoUninitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="eb7e1-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="eb7e1-103">`CoUninitializeEE` je zastaralá a neposkytuje žádné funkce.</span><span class="sxs-lookup"><span data-stu-id="eb7e1-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb7e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb7e1-104">Syntax</span></span>  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="eb7e1-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb7e1-105">Remarks</span></span>  
 <span data-ttu-id="eb7e1-106">Modul pro spuštění společného jazykového modulu runtime nelze uvolnit z procesu.</span><span class="sxs-lookup"><span data-stu-id="eb7e1-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="eb7e1-107">Pro vypnutí volání prováděcího modulu [CorExitProcess –](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="eb7e1-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb7e1-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb7e1-108">See also</span></span>

- [<span data-ttu-id="eb7e1-109">CoInitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="eb7e1-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)
- [<span data-ttu-id="eb7e1-110">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="eb7e1-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
