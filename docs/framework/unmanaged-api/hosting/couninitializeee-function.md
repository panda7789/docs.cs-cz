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
ms.openlocfilehash: ef5faff6682ed6c043e81212f2cb27d4cfbd813d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601854"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="7d580-102">CoUninitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="7d580-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="7d580-103">`CoUninitializeEE` je zastaralá a poskytuje žádné funkce.</span><span class="sxs-lookup"><span data-stu-id="7d580-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d580-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d580-104">Syntax</span></span>  
  
```  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="7d580-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d580-105">Remarks</span></span>  
 <span data-ttu-id="7d580-106">Common language runtime prováděcí modul nemůže být uvolněna z procesu.</span><span class="sxs-lookup"><span data-stu-id="7d580-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="7d580-107">Vypnout volání modulu provádění [corexitprocess –](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="7d580-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d580-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d580-108">See also</span></span>
- [<span data-ttu-id="7d580-109">CoInitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="7d580-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)
- [<span data-ttu-id="7d580-110">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="7d580-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
