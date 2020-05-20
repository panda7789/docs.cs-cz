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
ms.openlocfilehash: 006045ce101884119f676e4f6324815eb21a10a4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614653"
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="85fa5-102">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85fa5-102">ISymUnmanagedWriter3 Interface</span></span>
<span data-ttu-id="85fa5-103">Představuje zapisovač symbolů a poskytuje metody pro definování dokumentů, sekvenčních bodů, lexikálních oborů a proměnných.</span><span class="sxs-lookup"><span data-stu-id="85fa5-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="85fa5-104">Toto rozhraní rozšiřuje rozhraní [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="85fa5-104">This interface extends the [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="85fa5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="85fa5-105">Methods</span></span>  
  
|<span data-ttu-id="85fa5-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="85fa5-106">Method</span></span>|<span data-ttu-id="85fa5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="85fa5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85fa5-108">Commit – Metoda</span><span class="sxs-lookup"><span data-stu-id="85fa5-108">Commit Method</span></span>](isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="85fa5-109">Potvrdí změny, které byly doposud napsány do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="85fa5-109">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="85fa5-110">OpenMethod2 – metoda</span><span class="sxs-lookup"><span data-stu-id="85fa5-110">OpenMethod2 Method</span></span>](isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="85fa5-111">Otevře metodu a poskytne její skutečný posun oddílu v obrázku.</span><span class="sxs-lookup"><span data-stu-id="85fa5-111">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="85fa5-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="85fa5-112">Requirements</span></span>  
 <span data-ttu-id="85fa5-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="85fa5-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85fa5-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="85fa5-114">See also</span></span>

- [<span data-ttu-id="85fa5-115">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="85fa5-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="85fa5-116">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85fa5-116">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="85fa5-117">ISymUnmanagedWriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85fa5-117">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
