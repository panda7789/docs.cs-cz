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
ms.openlocfilehash: cbafe39fffd28a9bfccaa275c9009bc03549cda6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429425"
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="715ef-102">ISymUnmanagedWriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="715ef-102">ISymUnmanagedWriter2 Interface</span></span>
<span data-ttu-id="715ef-103">Reprezentuje zapisovač symbol a poskytuje metody k definování dokumenty, body sekvence, lexikální oborů a proměnné.</span><span class="sxs-lookup"><span data-stu-id="715ef-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="715ef-104">Toto rozhraní rozšiřuje [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="715ef-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="715ef-105">Metody</span><span class="sxs-lookup"><span data-stu-id="715ef-105">Methods</span></span>  
  
|<span data-ttu-id="715ef-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="715ef-106">Method</span></span>|<span data-ttu-id="715ef-107">Popis</span><span class="sxs-lookup"><span data-stu-id="715ef-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="715ef-108">DefineConstant2 – metoda</span><span class="sxs-lookup"><span data-stu-id="715ef-108">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="715ef-109">Definuje název pro konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="715ef-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="715ef-110">DefineGlobalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="715ef-110">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="715ef-111">Definuje jeden globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="715ef-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="715ef-112">DefineLocalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="715ef-112">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="715ef-113">V aktuálním oboru lexikální definuje jednu proměnnou.</span><span class="sxs-lookup"><span data-stu-id="715ef-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="715ef-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="715ef-114">Requirements</span></span>  
 <span data-ttu-id="715ef-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="715ef-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="715ef-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="715ef-116">See Also</span></span>  
 [<span data-ttu-id="715ef-117">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="715ef-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="715ef-118">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="715ef-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="715ef-119">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="715ef-119">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
