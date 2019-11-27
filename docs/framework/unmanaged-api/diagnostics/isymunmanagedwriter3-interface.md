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
ms.openlocfilehash: 115d4b58b01606c29719fb88ab7dbf5a858b1251
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438166"
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="abe2e-102">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="abe2e-102">ISymUnmanagedWriter3 Interface</span></span>
<span data-ttu-id="abe2e-103">Představuje zapisovač symbolů a poskytuje metody pro definování dokumentů, sekvenčních bodů, lexikálních oborů a proměnných.</span><span class="sxs-lookup"><span data-stu-id="abe2e-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="abe2e-104">Toto rozhraní rozšiřuje rozhraní [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="abe2e-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="abe2e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="abe2e-105">Methods</span></span>  
  
|<span data-ttu-id="abe2e-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="abe2e-106">Method</span></span>|<span data-ttu-id="abe2e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="abe2e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="abe2e-108">Commit – metoda</span><span class="sxs-lookup"><span data-stu-id="abe2e-108">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="abe2e-109">Potvrdí změny, které byly doposud napsány do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="abe2e-109">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="abe2e-110">OpenMethod2 – metoda</span><span class="sxs-lookup"><span data-stu-id="abe2e-110">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="abe2e-111">Otevře metodu a poskytne její skutečný posun oddílu v obrázku.</span><span class="sxs-lookup"><span data-stu-id="abe2e-111">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="abe2e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="abe2e-112">Requirements</span></span>  
 <span data-ttu-id="abe2e-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="abe2e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe2e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abe2e-114">See also</span></span>

- [<span data-ttu-id="abe2e-115">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="abe2e-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="abe2e-116">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="abe2e-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="abe2e-117">ISymUnmanagedWriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="abe2e-117">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
