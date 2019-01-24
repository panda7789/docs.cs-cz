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
ms.openlocfilehash: b19e5ce88ea34188b2757d2a0c313341fbf1e7e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604252"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="f4f3d-102">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4f3d-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="f4f3d-103">Představuje metodu v úložišti symbolů.</span><span class="sxs-lookup"><span data-stu-id="f4f3d-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="f4f3d-104">Toto rozhraní poskytuje přístup pouze na související symbol atributy metody, namísto atributy vztahující se k typu.</span><span class="sxs-lookup"><span data-stu-id="f4f3d-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f4f3d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f4f3d-105">Methods</span></span>  
  
|<span data-ttu-id="f4f3d-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f4f3d-106">Method</span></span>|<span data-ttu-id="f4f3d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f4f3d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f4f3d-108">GetNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="f4f3d-108">GetNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="f4f3d-109">Získá obor názvů, ve kterém je definována této metody.</span><span class="sxs-lookup"><span data-stu-id="f4f3d-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="f4f3d-110">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="f4f3d-110">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="f4f3d-111">Vrátí posunutí v rámci této metody, které odpovídá na dané pozici v rámci dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f4f3d-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="f4f3d-112">GetParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="f4f3d-112">GetParameters Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="f4f3d-113">Získá parametry pro tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="f4f3d-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="f4f3d-114">GetRanges – metoda</span><span class="sxs-lookup"><span data-stu-id="f4f3d-114">GetRanges Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="f4f3d-115">Danou pozici v dokumentu vrátí pole dvojic počáteční a koncové posunutí, které odpovídají na rozsahy jazyk Microsoft intermediate language (MSIL), která zahrnuje pozici v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="f4f3d-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="f4f3d-116">GetRootScope – metoda</span><span class="sxs-lookup"><span data-stu-id="f4f3d-116">GetRootScope Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="f4f3d-117">Získá kořenového oboru lexikální v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="f4f3d-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="f4f3d-118">Tento rozsah obklopuje celou metodu.</span><span class="sxs-lookup"><span data-stu-id="f4f3d-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="f4f3d-119">GetScopeFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="f4f3d-119">GetScopeFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="f4f3d-120">Získá nejvíce nadřazeného oboru lexikální v rámci této metody, které obklopuje dané posun.</span><span class="sxs-lookup"><span data-stu-id="f4f3d-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="f4f3d-121">GetSequencePointCount – metoda</span><span class="sxs-lookup"><span data-stu-id="f4f3d-121">GetSequencePointCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="f4f3d-122">Získá počet body sekvence v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="f4f3d-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="f4f3d-123">GetSequencePoints – metoda</span><span class="sxs-lookup"><span data-stu-id="f4f3d-123">GetSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="f4f3d-124">Získá všechny body sekvence v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="f4f3d-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="f4f3d-125">GetSourceStartEnd – metoda</span><span class="sxs-lookup"><span data-stu-id="f4f3d-125">GetSourceStartEnd Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="f4f3d-126">Získá počáteční a koncové pozice dokumentu pro zdroj této metody.</span><span class="sxs-lookup"><span data-stu-id="f4f3d-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="f4f3d-127">GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="f4f3d-127">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="f4f3d-128">Vrátí token metadat pro tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="f4f3d-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f4f3d-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f4f3d-129">Requirements</span></span>  
 <span data-ttu-id="f4f3d-130">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f4f3d-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4f3d-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4f3d-131">See also</span></span>
- [<span data-ttu-id="f4f3d-132">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="f4f3d-132">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
