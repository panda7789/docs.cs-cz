---
title: "ISymUnmanagedWriter3 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter3
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter3
helpviewer_keywords: ISymUnmanagedWriter3 interface [.NET Framework debugging]
ms.assetid: a034c21e-e371-4360-b470-29e88288948f
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 49928044bcf2c598cdc0e4315d569f2c4eb02f1d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="810c8-102">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="810c8-102">ISymUnmanagedWriter3 Interface</span></span>
<span data-ttu-id="810c8-103">Reprezentuje zapisovač symbol a poskytuje metody k definování dokumenty, body sekvence, lexikální oborů a proměnné.</span><span class="sxs-lookup"><span data-stu-id="810c8-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="810c8-104">Toto rozhraní rozšiřuje [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="810c8-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="810c8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="810c8-105">Methods</span></span>  
  
|<span data-ttu-id="810c8-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="810c8-106">Method</span></span>|<span data-ttu-id="810c8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="810c8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="810c8-108">Commit – metoda</span><span class="sxs-lookup"><span data-stu-id="810c8-108">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="810c8-109">Potvrdí změny dosavadní zapisovat do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="810c8-109">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="810c8-110">OpenMethod2 – metoda</span><span class="sxs-lookup"><span data-stu-id="810c8-110">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="810c8-111">Otevře metodu a poskytuje její skutečné části posun v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="810c8-111">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="810c8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="810c8-112">Requirements</span></span>  
 <span data-ttu-id="810c8-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="810c8-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="810c8-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="810c8-114">See Also</span></span>  
 [<span data-ttu-id="810c8-115">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="810c8-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="810c8-116">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="810c8-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="810c8-117">ISymUnmanagedWriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="810c8-117">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
