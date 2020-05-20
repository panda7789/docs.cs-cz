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
ms.openlocfilehash: 3bcb642ac62fb00780a4fda7aaeebaabb386db33
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615069"
---
# <a name="isymunmanagednamespace-interface"></a><span data-ttu-id="1d00e-102">ISymUnmanagedNamespace – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1d00e-102">ISymUnmanagedNamespace Interface</span></span>
<span data-ttu-id="1d00e-103">Představuje obor názvů.</span><span class="sxs-lookup"><span data-stu-id="1d00e-103">Represents a namespace.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1d00e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1d00e-104">Methods</span></span>  
  
|<span data-ttu-id="1d00e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1d00e-105">Method</span></span>|<span data-ttu-id="1d00e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1d00e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1d00e-107">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="1d00e-107">GetName Method</span></span>](isymunmanagednamespace-getname-method.md)|<span data-ttu-id="1d00e-108">Získá název tohoto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1d00e-108">Gets the name of this namespace.</span></span>|  
|[<span data-ttu-id="1d00e-109">GetNamespaces – metoda</span><span class="sxs-lookup"><span data-stu-id="1d00e-109">GetNamespaces Method</span></span>](isymunmanagednamespace-getnamespaces-method.md)|<span data-ttu-id="1d00e-110">Získá podřízené objekty tohoto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1d00e-110">Gets the children of this namespace.</span></span>|  
|[<span data-ttu-id="1d00e-111">GetVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="1d00e-111">GetVariables Method</span></span>](isymunmanagednamespace-getvariables-method.md)|<span data-ttu-id="1d00e-112">Vrátí všechny proměnné definované v globálním oboru v rámci tohoto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1d00e-112">Returns all variables defined at global scope within this namespace.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1d00e-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1d00e-113">Requirements</span></span>  
 <span data-ttu-id="1d00e-114">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1d00e-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d00e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d00e-115">See also</span></span>

- [<span data-ttu-id="1d00e-116">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="1d00e-116">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
