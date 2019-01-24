---
title: ISymUnmanagedWriter2 – rozhraní
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 99e8b8bbb25bc55c7d4f2f44aac8e24210d30b83
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560542"
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="7ea5b-102">ISymUnmanagedWriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ea5b-102">ISymUnmanagedWriter2 Interface</span></span>
<span data-ttu-id="7ea5b-103">Reprezentuje zapisovač symbolů a poskytuje metody, které definují dokumenty, body sekvence, lexikální obory a proměnné.</span><span class="sxs-lookup"><span data-stu-id="7ea5b-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="7ea5b-104">Toto rozhraní rozšiřuje [isymunmanagedwriter –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7ea5b-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ea5b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7ea5b-105">Methods</span></span>  
  
|<span data-ttu-id="7ea5b-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="7ea5b-106">Method</span></span>|<span data-ttu-id="7ea5b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7ea5b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7ea5b-108">DefineConstant2 – metoda</span><span class="sxs-lookup"><span data-stu-id="7ea5b-108">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="7ea5b-109">Definuje název pro konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7ea5b-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="7ea5b-110">DefineGlobalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="7ea5b-110">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="7ea5b-111">Definuje jeden globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="7ea5b-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="7ea5b-112">DefineLocalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="7ea5b-112">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="7ea5b-113">V aktuálním oboru lexikální definuje jednu proměnnou.</span><span class="sxs-lookup"><span data-stu-id="7ea5b-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7ea5b-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ea5b-114">Requirements</span></span>  
 <span data-ttu-id="7ea5b-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7ea5b-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ea5b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ea5b-116">See also</span></span>
- [<span data-ttu-id="7ea5b-117">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="7ea5b-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="7ea5b-118">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ea5b-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="7ea5b-119">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ea5b-119">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
