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
ms.openlocfilehash: 97df6d6ec9a446e89eef8a9f8a5e5e8ddc85c0f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127397"
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="aa860-102">ISymUnmanagedWriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa860-102">ISymUnmanagedWriter2 Interface</span></span>
<span data-ttu-id="aa860-103">Reprezentuje zapisovač symbolů a poskytuje metody, které definují dokumenty, body sekvence, lexikální obory a proměnné.</span><span class="sxs-lookup"><span data-stu-id="aa860-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="aa860-104">Toto rozhraní rozšiřuje [isymunmanagedwriter –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aa860-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aa860-105">Metody</span><span class="sxs-lookup"><span data-stu-id="aa860-105">Methods</span></span>  
  
|<span data-ttu-id="aa860-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="aa860-106">Method</span></span>|<span data-ttu-id="aa860-107">Popis</span><span class="sxs-lookup"><span data-stu-id="aa860-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aa860-108">DefineConstant2 – metoda</span><span class="sxs-lookup"><span data-stu-id="aa860-108">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="aa860-109">Definuje název pro konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="aa860-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="aa860-110">DefineGlobalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="aa860-110">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="aa860-111">Definuje jeden globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="aa860-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="aa860-112">DefineLocalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="aa860-112">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="aa860-113">V aktuálním oboru lexikální definuje jednu proměnnou.</span><span class="sxs-lookup"><span data-stu-id="aa860-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aa860-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aa860-114">Requirements</span></span>  
 <span data-ttu-id="aa860-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="aa860-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa860-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa860-116">See also</span></span>

- [<span data-ttu-id="aa860-117">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="aa860-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="aa860-118">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa860-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="aa860-119">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa860-119">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
