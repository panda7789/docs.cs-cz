---
title: "EndMerge – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.EndMerge
- EndMerge
api_location: alink.dll
api_type: COM
f1_keywords: EndMerge
helpviewer_keywords: EndMerge method
ms.assetid: 1d03bb15-a2c8-4a04-8fc6-b126c89c3778
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58e9cecae43fb69f1ce2e90eb9d6551d287ca7b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="endmerge-method"></a><span data-ttu-id="7aca3-102">EndMerge – metoda</span><span class="sxs-lookup"><span data-stu-id="7aca3-102">EndMerge Method</span></span>
<span data-ttu-id="7aca3-103">Označuje, že byly všechny vlastní atributy sloučeny do oboru vysílat.</span><span class="sxs-lookup"><span data-stu-id="7aca3-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aca3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7aca3-104">Syntax</span></span>  
  
```  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7aca3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7aca3-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="7aca3-106">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="7aca3-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7aca3-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7aca3-107">Return Value</span></span>  
 <span data-ttu-id="7aca3-108">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="7aca3-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7aca3-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7aca3-109">Requirements</span></span>  
 <span data-ttu-id="7aca3-110">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="7aca3-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aca3-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="7aca3-111">See Also</span></span>  
 [<span data-ttu-id="7aca3-112">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7aca3-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="7aca3-113">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7aca3-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="7aca3-114">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="7aca3-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
