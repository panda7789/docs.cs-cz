---
title: ISymUnmanagedWriter3 – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3
helpviewer_keywords:
- ISymUnmanagedWriter3 interface [.NET Framework debugging]
ms.assetid: a034c21e-e371-4360-b470-29e88288948f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e26d79a5b597b8585f2fffd7f3945f00832ca134
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138447"
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="0242c-102">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0242c-102">ISymUnmanagedWriter3 Interface</span></span>
<span data-ttu-id="0242c-103">Reprezentuje zapisovač symbolů a poskytuje metody, které definují dokumenty, body sekvence, lexikální obory a proměnné.</span><span class="sxs-lookup"><span data-stu-id="0242c-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="0242c-104">Toto rozhraní rozšiřuje [isymunmanagedwriter –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0242c-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0242c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0242c-105">Methods</span></span>  
  
|<span data-ttu-id="0242c-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="0242c-106">Method</span></span>|<span data-ttu-id="0242c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0242c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0242c-108">Commit – metoda</span><span class="sxs-lookup"><span data-stu-id="0242c-108">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="0242c-109">Potvrdí změny doposud zapsán do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="0242c-109">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="0242c-110">OpenMethod2 – metoda</span><span class="sxs-lookup"><span data-stu-id="0242c-110">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="0242c-111">Otevře metodu a poskytuje skutečné části posun v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="0242c-111">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0242c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0242c-112">Requirements</span></span>  
 <span data-ttu-id="0242c-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0242c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0242c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0242c-114">See also</span></span>

- [<span data-ttu-id="0242c-115">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="0242c-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="0242c-116">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0242c-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="0242c-117">ISymUnmanagedWriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0242c-117">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
