---
title: "SetAssemblyProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.SetAssemblyProps
api_location: alink.dll
api_type: COM
f1_keywords: SetAssemblyProps
helpviewer_keywords: SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0245b6b1e30174bb3496d3d6ab674ccc00fb9fee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="14800-102">SetAssemblyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="14800-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="14800-103">Přiřadí vlastnosti úrovni sestavení.</span><span class="sxs-lookup"><span data-stu-id="14800-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14800-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14800-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="14800-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14800-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="14800-106">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="14800-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="14800-107">Soubor, který definuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="14800-107">File that defines the property.</span></span> <span data-ttu-id="14800-108">Může mít hodnotu NULL, pokud `AssemblyID` neindikuje nevázaný netmodule.</span><span class="sxs-lookup"><span data-stu-id="14800-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="14800-109">Určuje možnost upravit.</span><span class="sxs-lookup"><span data-stu-id="14800-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="14800-110">Nová hodnota možnosti.</span><span class="sxs-lookup"><span data-stu-id="14800-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14800-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="14800-111">Return Value</span></span>  
 <span data-ttu-id="14800-112">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="14800-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14800-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14800-113">Requirements</span></span>  
 <span data-ttu-id="14800-114">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="14800-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14800-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="14800-115">See Also</span></span>  
 [<span data-ttu-id="14800-116">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="14800-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="14800-117">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="14800-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="14800-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="14800-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
