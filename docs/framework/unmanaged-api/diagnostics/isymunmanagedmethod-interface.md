---
title: "ISymUnmanagedMethod – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod
helpviewer_keywords: ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b6305625c3d02dbd126a284287e19b319e21eeba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="c7643-102">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c7643-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="c7643-103">Představuje metodu v rámci úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="c7643-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="c7643-104">Toto rozhraní poskytuje přístup k pouze související symbol atributy metody, místo atributy související s typem.</span><span class="sxs-lookup"><span data-stu-id="c7643-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7643-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c7643-105">Methods</span></span>  
  
|<span data-ttu-id="c7643-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="c7643-106">Method</span></span>|<span data-ttu-id="c7643-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c7643-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7643-108">GetNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="c7643-108">GetNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="c7643-109">Získá obor názvů, ve kterém je tato metoda definována.</span><span class="sxs-lookup"><span data-stu-id="c7643-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="c7643-110">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="c7643-110">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="c7643-111">Vrátí posunutí v rámci této metody, které odpovídá na dané pozici v rámci dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c7643-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="c7643-112">GetParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="c7643-112">GetParameters Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="c7643-113">Získá parametry pro tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="c7643-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="c7643-114">GetRanges – metoda</span><span class="sxs-lookup"><span data-stu-id="c7643-114">GetRanges Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="c7643-115">Dané pozici v dokumentu vrátí pole počáteční a koncové posunutí párů, které odpovídají na rozsahy Microsoft (MSIL intermediate language) pokrývající pozici v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="c7643-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="c7643-116">GetRootScope – metoda</span><span class="sxs-lookup"><span data-stu-id="c7643-116">GetRootScope Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="c7643-117">Získá lexikální kořenovém oboru v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="c7643-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="c7643-118">Tento obor uzavře celý metoda.</span><span class="sxs-lookup"><span data-stu-id="c7643-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="c7643-119">GetScopeFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="c7643-119">GetScopeFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="c7643-120">Získá lexikální nejvíce vymezeném oboru v rámci této metody, která obklopuje daným posunem.</span><span class="sxs-lookup"><span data-stu-id="c7643-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="c7643-121">GetSequencePointCount – metoda</span><span class="sxs-lookup"><span data-stu-id="c7643-121">GetSequencePointCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="c7643-122">Získá počet bodů pořadí v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="c7643-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="c7643-123">GetSequencePoints – metoda</span><span class="sxs-lookup"><span data-stu-id="c7643-123">GetSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="c7643-124">Získá všechny body pořadí v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="c7643-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="c7643-125">GetSourceStartEnd – metoda</span><span class="sxs-lookup"><span data-stu-id="c7643-125">GetSourceStartEnd Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="c7643-126">Získá počáteční a koncové pozice dokumentu pro zdroj této metody.</span><span class="sxs-lookup"><span data-stu-id="c7643-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="c7643-127">GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="c7643-127">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="c7643-128">Vrátí metadata token tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="c7643-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c7643-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7643-129">Requirements</span></span>  
 <span data-ttu-id="c7643-130">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c7643-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7643-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7643-131">See Also</span></span>  
 [<span data-ttu-id="c7643-132">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="c7643-132">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
