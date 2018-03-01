---
title: "ISymUnmanagedWriter2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedWriter2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2
helpviewer_keywords:
- ISymUnmanagedWriter2 interface [.NET Framework debugging]
ms.assetid: 8e78faa4-cf43-44fb-a91d-94d6df692a25
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 98461cd2c2bc26d78f3f3f747b95d46576ba01e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="9cbf8-102">ISymUnmanagedWriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9cbf8-102">ISymUnmanagedWriter2 Interface</span></span>
<span data-ttu-id="9cbf8-103">Reprezentuje zapisovač symbol a poskytuje metody k definování dokumenty, body sekvence, lexikální oborů a proměnné.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="9cbf8-104">Toto rozhraní rozšiřuje [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9cbf8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9cbf8-105">Methods</span></span>  
  
|<span data-ttu-id="9cbf8-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="9cbf8-106">Method</span></span>|<span data-ttu-id="9cbf8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9cbf8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9cbf8-108">DefineConstant2 – metoda</span><span class="sxs-lookup"><span data-stu-id="9cbf8-108">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="9cbf8-109">Definuje název pro konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="9cbf8-110">DefineGlobalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="9cbf8-110">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="9cbf8-111">Definuje jeden globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="9cbf8-112">DefineLocalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="9cbf8-112">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="9cbf8-113">V aktuálním oboru lexikální definuje jednu proměnnou.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9cbf8-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9cbf8-114">Requirements</span></span>  
 <span data-ttu-id="9cbf8-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9cbf8-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cbf8-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9cbf8-116">See Also</span></span>  
 [<span data-ttu-id="9cbf8-117">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="9cbf8-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="9cbf8-118">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9cbf8-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="9cbf8-119">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9cbf8-119">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
