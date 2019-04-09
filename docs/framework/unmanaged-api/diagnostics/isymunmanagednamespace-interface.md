---
title: ISymUnmanagedNamespace – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace
helpviewer_keywords:
- ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: d42bea4e-5848-4e43-a883-69af7a313ce9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87dd6db9624c2216ab13e77b04cfa63f95aee7e2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183310"
---
# <a name="isymunmanagednamespace-interface"></a><span data-ttu-id="46009-102">ISymUnmanagedNamespace – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46009-102">ISymUnmanagedNamespace Interface</span></span>
<span data-ttu-id="46009-103">Představuje obor názvů.</span><span class="sxs-lookup"><span data-stu-id="46009-103">Represents a namespace.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="46009-104">Metody</span><span class="sxs-lookup"><span data-stu-id="46009-104">Methods</span></span>  
  
|<span data-ttu-id="46009-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="46009-105">Method</span></span>|<span data-ttu-id="46009-106">Popis</span><span class="sxs-lookup"><span data-stu-id="46009-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="46009-107">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="46009-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-getname-method.md)|<span data-ttu-id="46009-108">Získá název tohoto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="46009-108">Gets the name of this namespace.</span></span>|  
|[<span data-ttu-id="46009-109">GetNamespaces – metoda</span><span class="sxs-lookup"><span data-stu-id="46009-109">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-getnamespaces-method.md)|<span data-ttu-id="46009-110">Získá podřízené objekty tohoto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="46009-110">Gets the children of this namespace.</span></span>|  
|[<span data-ttu-id="46009-111">GetVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="46009-111">GetVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-getvariables-method.md)|<span data-ttu-id="46009-112">Vrátí všechny proměnné definované v globálním oboru v rámci tohoto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="46009-112">Returns all variables defined at global scope within this namespace.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="46009-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="46009-113">Requirements</span></span>  
 <span data-ttu-id="46009-114">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="46009-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46009-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46009-115">See also</span></span>

- [<span data-ttu-id="46009-116">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="46009-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
