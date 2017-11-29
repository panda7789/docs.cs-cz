---
title: "EmitAssembly – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location: alink.dll
api_type: COM
f1_keywords: EmitAssembly
helpviewer_keywords: EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3471c4ad2d06443e0f05dc344be5f791817f2d2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="emitassembly-method"></a><span data-ttu-id="d4b0b-102">EmitAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="d4b0b-102">EmitAssembly Method</span></span>
<span data-ttu-id="d4b0b-103">Vytvoří sestavení.</span><span class="sxs-lookup"><span data-stu-id="d4b0b-103">Creates the assembly.</span></span> <span data-ttu-id="d4b0b-104">Volejte tuto metodu po zavřeny všechny ostatní soubory s výjimkou souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="d4b0b-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="d4b0b-105">Tato metoda není volána při vytváření nevázaný moduly.</span><span class="sxs-lookup"><span data-stu-id="d4b0b-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4b0b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4b0b-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4b0b-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4b0b-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d4b0b-108">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="d4b0b-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4b0b-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d4b0b-109">Return Value</span></span>  
 <span data-ttu-id="d4b0b-110">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="d4b0b-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4b0b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4b0b-111">Requirements</span></span>  
 <span data-ttu-id="d4b0b-112">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="d4b0b-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4b0b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4b0b-113">See Also</span></span>  
 [<span data-ttu-id="d4b0b-114">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4b0b-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="d4b0b-115">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4b0b-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="d4b0b-116">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="d4b0b-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
