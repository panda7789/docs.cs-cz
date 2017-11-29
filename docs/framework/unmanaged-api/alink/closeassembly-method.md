---
title: "CloseAssembly – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.CloseAssembly
- CloseAssembly
api_location: alink.dll
api_type: COM
f1_keywords: CloseAssembly
helpviewer_keywords: CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: be68348b619f342eca4841a6052088bf7152f453
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="closeassembly-method"></a><span data-ttu-id="87c54-102">CloseAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="87c54-102">CloseAssembly Method</span></span>
<span data-ttu-id="87c54-103">Dokončí operace sestavení.</span><span class="sxs-lookup"><span data-stu-id="87c54-103">Finalizes assembly operations.</span></span> <span data-ttu-id="87c54-104">Tuto metodu volejte před zahájením nové sestavení nebo nevázaný modulu.</span><span class="sxs-lookup"><span data-stu-id="87c54-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87c54-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87c54-105">Syntax</span></span>  
  
```  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87c54-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="87c54-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="87c54-107">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="87c54-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87c54-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="87c54-108">Return Value</span></span>  
 <span data-ttu-id="87c54-109">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="87c54-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87c54-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="87c54-110">Requirements</span></span>  
 <span data-ttu-id="87c54-111">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="87c54-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87c54-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="87c54-112">See Also</span></span>  
 [<span data-ttu-id="87c54-113">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87c54-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="87c54-114">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87c54-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="87c54-115">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="87c54-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
