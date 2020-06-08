---
title: CoInitializeCor – funkce
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeCor
helpviewer_keywords:
- CoInitializeCor function [.NET Framework hosting]
ms.assetid: 9b9079fb-579e-4141-b3f0-791072dd40dc
topic_type:
- apiref
ms.openlocfilehash: 1263467fc5db92d4dd21c4f09a98af309e2c4d55
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504417"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="a1324-102">CoInitializeCor – funkce</span><span class="sxs-lookup"><span data-stu-id="a1324-102">CoInitializeCor Function</span></span>
<span data-ttu-id="a1324-103">`CoInitializeCor`je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="a1324-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1324-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1324-104">Syntax</span></span>  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="a1324-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1324-105">Remarks</span></span>  
 <span data-ttu-id="a1324-106">Chcete-li inicializovat modul CLR (Common Language Runtime), použijte buď [CorBindToRuntimeEx –](corbindtoruntimeex-function.md) nebo [CorBindToCurrentRuntime –](corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="a1324-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1324-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1324-107">Requirements</span></span>  
 <span data-ttu-id="a1324-108">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a1324-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1324-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1324-109">See also</span></span>

- [<span data-ttu-id="a1324-110">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="a1324-110">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
