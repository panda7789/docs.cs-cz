---
title: "GetResolutionScope – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.GetResolutionScope
api_location: alink.dll
api_type: COM
f1_keywords: GetResolutionScope
helpviewer_keywords: GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f9dc63a7165ab472e973e0bc4f3e4cbb99e5d828
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="f8bc8-102">GetResolutionScope – metoda</span><span class="sxs-lookup"><span data-stu-id="f8bc8-102">GetResolutionScope Method</span></span>
<span data-ttu-id="f8bc8-103">Načte oboru daného typu.</span><span class="sxs-lookup"><span data-stu-id="f8bc8-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8bc8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8bc8-104">Syntax</span></span>  
  
```  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8bc8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8bc8-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f8bc8-106">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="f8bc8-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="f8bc8-107">Soubor, který je potřeba zkontrolovat odkaz.</span><span class="sxs-lookup"><span data-stu-id="f8bc8-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="f8bc8-108">Token souboru tento typ je definována v, obvykle načíst s [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="f8bc8-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="f8bc8-109">Obdrží sestavení nebo odkaz na modul.</span><span class="sxs-lookup"><span data-stu-id="f8bc8-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8bc8-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f8bc8-110">Return Value</span></span>  
 <span data-ttu-id="f8bc8-111">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="f8bc8-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8bc8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8bc8-112">Requirements</span></span>  
 <span data-ttu-id="f8bc8-113">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="f8bc8-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8bc8-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8bc8-114">See Also</span></span>  
 [<span data-ttu-id="f8bc8-115">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8bc8-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f8bc8-116">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8bc8-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="f8bc8-117">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="f8bc8-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
