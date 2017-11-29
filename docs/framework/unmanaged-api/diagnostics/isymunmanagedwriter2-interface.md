---
title: "ISymUnmanagedWriter2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter2
helpviewer_keywords: ISymUnmanagedWriter2 interface [.NET Framework debugging]
ms.assetid: 8e78faa4-cf43-44fb-a91d-94d6df692a25
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bd297a8ee0172f1624e6983de9bc9bf25bd86621
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="ce547-102">ISymUnmanagedWriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ce547-102">ISymUnmanagedWriter2 Interface</span></span>
<span data-ttu-id="ce547-103">Reprezentuje zapisovač symbol a poskytuje metody k definování dokumenty, body sekvence, lexikální oborů a proměnné.</span><span class="sxs-lookup"><span data-stu-id="ce547-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="ce547-104">Toto rozhraní rozšiřuje [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ce547-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ce547-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ce547-105">Methods</span></span>  
  
|<span data-ttu-id="ce547-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="ce547-106">Method</span></span>|<span data-ttu-id="ce547-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ce547-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ce547-108">Defineconstant2 – metoda</span><span class="sxs-lookup"><span data-stu-id="ce547-108">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="ce547-109">Definuje název pro konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ce547-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="ce547-110">Defineglobalvariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="ce547-110">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="ce547-111">Definuje jeden globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="ce547-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="ce547-112">Definelocalvariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="ce547-112">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="ce547-113">V aktuálním oboru lexikální definuje jednu proměnnou.</span><span class="sxs-lookup"><span data-stu-id="ce547-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ce547-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ce547-114">Requirements</span></span>  
 <span data-ttu-id="ce547-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ce547-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce547-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce547-116">See Also</span></span>  
 [<span data-ttu-id="ce547-117">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="ce547-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="ce547-118">ISymUnmanagedWriter – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="ce547-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="ce547-119">ISymUnmanagedWriter3 – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="ce547-119">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
