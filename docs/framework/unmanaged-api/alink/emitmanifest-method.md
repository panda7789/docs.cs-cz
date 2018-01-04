---
title: "EmitManifest – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EmitManifest
- IALink.EmitManifest
api_location: alink.dll
api_type: COM
f1_keywords: EmitManifest
helpviewer_keywords: EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 11966eccfdbbdbab29d305915afd904a54f9c57b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="emitmanifest-method"></a><span data-ttu-id="b28bc-102">EmitManifest – metoda</span><span class="sxs-lookup"><span data-stu-id="b28bc-102">EmitManifest Method</span></span>
<span data-ttu-id="b28bc-103">Vysílá konečné manifestu.</span><span class="sxs-lookup"><span data-stu-id="b28bc-103">Emits the final manifest.</span></span> <span data-ttu-id="b28bc-104">Tuto metodu volejte po importu všechny ostatní soubory a nastavení všech možností.</span><span class="sxs-lookup"><span data-stu-id="b28bc-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="b28bc-105">Nevolejte tuto metodu pro nevázaný moduly.</span><span class="sxs-lookup"><span data-stu-id="b28bc-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b28bc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b28bc-106">Syntax</span></span>  
  
```  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b28bc-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="b28bc-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b28bc-108">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="b28bc-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="b28bc-109">Obdrží velikost tak, aby vyhradil v souboru sestavení načítají [strongnamesignaturesize – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="b28bc-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="b28bc-110">Volitelně přijme token manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="b28bc-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b28bc-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b28bc-111">Return Value</span></span>  
 <span data-ttu-id="b28bc-112">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="b28bc-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b28bc-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b28bc-113">Requirements</span></span>  
 <span data-ttu-id="b28bc-114">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="b28bc-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b28bc-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="b28bc-115">See Also</span></span>  
 [<span data-ttu-id="b28bc-116">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b28bc-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="b28bc-117">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b28bc-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="b28bc-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="b28bc-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
