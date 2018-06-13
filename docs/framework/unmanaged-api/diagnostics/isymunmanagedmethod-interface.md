---
title: ISymUnmanagedMethod – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod
helpviewer_keywords:
- ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 728acc09f739fe567fca4a2571cbabf1ba8838a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427428"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="a1a61-102">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1a61-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="a1a61-103">Představuje metodu v rámci úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="a1a61-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="a1a61-104">Toto rozhraní poskytuje přístup k pouze související symbol atributy metody, místo atributy související s typem.</span><span class="sxs-lookup"><span data-stu-id="a1a61-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1a61-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a1a61-105">Methods</span></span>  
  
|<span data-ttu-id="a1a61-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="a1a61-106">Method</span></span>|<span data-ttu-id="a1a61-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a1a61-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a1a61-108">GetNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="a1a61-108">GetNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="a1a61-109">Získá obor názvů, ve kterém je tato metoda definována.</span><span class="sxs-lookup"><span data-stu-id="a1a61-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="a1a61-110">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="a1a61-110">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="a1a61-111">Vrátí posunutí v rámci této metody, které odpovídá na dané pozici v rámci dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a1a61-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="a1a61-112">GetParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="a1a61-112">GetParameters Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="a1a61-113">Získá parametry pro tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="a1a61-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="a1a61-114">GetRanges – metoda</span><span class="sxs-lookup"><span data-stu-id="a1a61-114">GetRanges Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="a1a61-115">Dané pozici v dokumentu vrátí pole počáteční a koncové posunutí párů, které odpovídají na rozsahy Microsoft (MSIL intermediate language) pokrývající pozici v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="a1a61-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="a1a61-116">GetRootScope – metoda</span><span class="sxs-lookup"><span data-stu-id="a1a61-116">GetRootScope Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="a1a61-117">Získá lexikální kořenovém oboru v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="a1a61-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="a1a61-118">Tento obor uzavře celý metoda.</span><span class="sxs-lookup"><span data-stu-id="a1a61-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="a1a61-119">GetScopeFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="a1a61-119">GetScopeFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="a1a61-120">Získá lexikální nejvíce vymezeném oboru v rámci této metody, která obklopuje daným posunem.</span><span class="sxs-lookup"><span data-stu-id="a1a61-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="a1a61-121">GetSequencePointCount – metoda</span><span class="sxs-lookup"><span data-stu-id="a1a61-121">GetSequencePointCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="a1a61-122">Získá počet bodů pořadí v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="a1a61-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="a1a61-123">GetSequencePoints – metoda</span><span class="sxs-lookup"><span data-stu-id="a1a61-123">GetSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="a1a61-124">Získá všechny body pořadí v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="a1a61-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="a1a61-125">GetSourceStartEnd – metoda</span><span class="sxs-lookup"><span data-stu-id="a1a61-125">GetSourceStartEnd Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="a1a61-126">Získá počáteční a koncové pozice dokumentu pro zdroj této metody.</span><span class="sxs-lookup"><span data-stu-id="a1a61-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="a1a61-127">GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="a1a61-127">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="a1a61-128">Vrátí metadata token tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="a1a61-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a1a61-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1a61-129">Requirements</span></span>  
 <span data-ttu-id="a1a61-130">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a1a61-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1a61-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1a61-131">See Also</span></span>  
 [<span data-ttu-id="a1a61-132">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="a1a61-132">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
