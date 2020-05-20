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
ms.openlocfilehash: 1fe6055d930c6d30e947d6bc774d0520a9e175ae
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614679"
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="dd2d6-102">ISymUnmanagedWriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd2d6-102">ISymUnmanagedWriter2 Interface</span></span>
<span data-ttu-id="dd2d6-103">Představuje zapisovač symbolů a poskytuje metody pro definování dokumentů, sekvenčních bodů, lexikálních oborů a proměnných.</span><span class="sxs-lookup"><span data-stu-id="dd2d6-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="dd2d6-104">Toto rozhraní rozšiřuje rozhraní [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="dd2d6-104">This interface extends the [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dd2d6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="dd2d6-105">Methods</span></span>  
  
|<span data-ttu-id="dd2d6-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="dd2d6-106">Method</span></span>|<span data-ttu-id="dd2d6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="dd2d6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dd2d6-108">DefineConstant2 – metoda</span><span class="sxs-lookup"><span data-stu-id="dd2d6-108">DefineConstant2 Method</span></span>](isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="dd2d6-109">Definuje název pro konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dd2d6-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="dd2d6-110">DefineGlobalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="dd2d6-110">DefineGlobalVariable2 Method</span></span>](isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="dd2d6-111">Definuje jednu globální proměnnou.</span><span class="sxs-lookup"><span data-stu-id="dd2d6-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="dd2d6-112">DefineLocalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="dd2d6-112">DefineLocalVariable2 Method</span></span>](isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="dd2d6-113">Definuje jednu proměnnou v aktuálním lexikálním oboru.</span><span class="sxs-lookup"><span data-stu-id="dd2d6-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dd2d6-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd2d6-114">Requirements</span></span>  
 <span data-ttu-id="dd2d6-115">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="dd2d6-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd2d6-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd2d6-116">See also</span></span>

- [<span data-ttu-id="dd2d6-117">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="dd2d6-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="dd2d6-118">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd2d6-118">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="dd2d6-119">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd2d6-119">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
