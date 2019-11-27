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
ms.openlocfilehash: 1d3ccb2265f056d5776199d997dc067c8d5513e5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448781"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="a498b-102">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a498b-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="a498b-103">Představuje metodu v úložišti symbolů.</span><span class="sxs-lookup"><span data-stu-id="a498b-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="a498b-104">Toto rozhraní poskytuje přístup pouze k atributům, které se vztahují k symbolům metody, namísto atributů souvisejících s typem.</span><span class="sxs-lookup"><span data-stu-id="a498b-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a498b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a498b-105">Methods</span></span>  
  
|<span data-ttu-id="a498b-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="a498b-106">Method</span></span>|<span data-ttu-id="a498b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a498b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a498b-108">GetNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="a498b-108">GetNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="a498b-109">Získá obor názvů, ve kterém je tato metoda definována.</span><span class="sxs-lookup"><span data-stu-id="a498b-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="a498b-110">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="a498b-110">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="a498b-111">Vrátí posun v rámci této metody, který odpovídá dané pozici v rámci dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a498b-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="a498b-112">GetParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="a498b-112">GetParameters Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="a498b-113">Získá parametry pro tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="a498b-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="a498b-114">GetRanges – metoda</span><span class="sxs-lookup"><span data-stu-id="a498b-114">GetRanges Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="a498b-115">Vzhledem k pozici v dokumentu vrátí pole párů počátečního a koncového posunu, které odpovídají rozsahům v rámci této metody, které odpovídají rozsahům jazyka MSIL (Microsoft Intermediate Language), které umístění pokrývá.</span><span class="sxs-lookup"><span data-stu-id="a498b-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="a498b-116">GetRootScope – metoda</span><span class="sxs-lookup"><span data-stu-id="a498b-116">GetRootScope Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="a498b-117">Získá kořenový lexikální rozsah v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="a498b-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="a498b-118">Tento obor uzavírá celou metodu.</span><span class="sxs-lookup"><span data-stu-id="a498b-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="a498b-119">GetScopeFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="a498b-119">GetScopeFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="a498b-120">Získá nejvíce ohraničující lexikální obor v rámci této metody, která uzavře daný posun.</span><span class="sxs-lookup"><span data-stu-id="a498b-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="a498b-121">GetSequencePointCount – metoda</span><span class="sxs-lookup"><span data-stu-id="a498b-121">GetSequencePointCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="a498b-122">Získá počet bodů sekvence v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="a498b-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="a498b-123">GetSequencePoints – metoda</span><span class="sxs-lookup"><span data-stu-id="a498b-123">GetSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="a498b-124">Načte všechny body sekvence v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="a498b-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="a498b-125">GetSourceStartEnd – metoda</span><span class="sxs-lookup"><span data-stu-id="a498b-125">GetSourceStartEnd Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="a498b-126">Získá pozice počátečního a koncového dokumentu pro zdroj této metody.</span><span class="sxs-lookup"><span data-stu-id="a498b-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="a498b-127">GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="a498b-127">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="a498b-128">Vrátí token metadat pro tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="a498b-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a498b-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a498b-129">Requirements</span></span>  
 <span data-ttu-id="a498b-130">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a498b-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a498b-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a498b-131">See also</span></span>

- [<span data-ttu-id="a498b-132">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="a498b-132">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
