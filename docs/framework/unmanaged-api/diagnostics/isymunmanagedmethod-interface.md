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
ms.openlocfilehash: 7a98a0c40f68cef9bab1ea2de0850208aaef77a0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615121"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="c20a6-102">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c20a6-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="c20a6-103">Představuje metodu v úložišti symbolů.</span><span class="sxs-lookup"><span data-stu-id="c20a6-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="c20a6-104">Toto rozhraní poskytuje přístup pouze k atributům, které se vztahují k symbolům metody, namísto atributů souvisejících s typem.</span><span class="sxs-lookup"><span data-stu-id="c20a6-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c20a6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c20a6-105">Methods</span></span>  
  
|<span data-ttu-id="c20a6-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="c20a6-106">Method</span></span>|<span data-ttu-id="c20a6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c20a6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c20a6-108">GetNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="c20a6-108">GetNamespace Method</span></span>](isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="c20a6-109">Získá obor názvů, ve kterém je tato metoda definována.</span><span class="sxs-lookup"><span data-stu-id="c20a6-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="c20a6-110">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="c20a6-110">GetOffset Method</span></span>](isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="c20a6-111">Vrátí posun v rámci této metody, který odpovídá dané pozici v rámci dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c20a6-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="c20a6-112">GetParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="c20a6-112">GetParameters Method</span></span>](isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="c20a6-113">Získá parametry pro tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="c20a6-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="c20a6-114">GetRanges – metoda</span><span class="sxs-lookup"><span data-stu-id="c20a6-114">GetRanges Method</span></span>](isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="c20a6-115">Vzhledem k pozici v dokumentu vrátí pole párů počátečního a koncového posunu, které odpovídají rozsahům v rámci této metody, které odpovídají rozsahům jazyka MSIL (Microsoft Intermediate Language), které umístění pokrývá.</span><span class="sxs-lookup"><span data-stu-id="c20a6-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="c20a6-116">GetRootScope – metoda</span><span class="sxs-lookup"><span data-stu-id="c20a6-116">GetRootScope Method</span></span>](isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="c20a6-117">Získá kořenový lexikální rozsah v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="c20a6-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="c20a6-118">Tento obor uzavírá celou metodu.</span><span class="sxs-lookup"><span data-stu-id="c20a6-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="c20a6-119">GetScopeFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="c20a6-119">GetScopeFromOffset Method</span></span>](isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="c20a6-120">Získá nejvíce ohraničující lexikální obor v rámci této metody, která uzavře daný posun.</span><span class="sxs-lookup"><span data-stu-id="c20a6-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="c20a6-121">GetSequencePointCount – metoda</span><span class="sxs-lookup"><span data-stu-id="c20a6-121">GetSequencePointCount Method</span></span>](isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="c20a6-122">Získá počet bodů sekvence v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="c20a6-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="c20a6-123">GetSequencePoints – metoda</span><span class="sxs-lookup"><span data-stu-id="c20a6-123">GetSequencePoints Method</span></span>](isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="c20a6-124">Načte všechny body sekvence v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="c20a6-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="c20a6-125">GetSourceStartEnd – metoda</span><span class="sxs-lookup"><span data-stu-id="c20a6-125">GetSourceStartEnd Method</span></span>](isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="c20a6-126">Získá pozice počátečního a koncového dokumentu pro zdroj této metody.</span><span class="sxs-lookup"><span data-stu-id="c20a6-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="c20a6-127">GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="c20a6-127">GetToken Method</span></span>](isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="c20a6-128">Vrátí token metadat pro tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="c20a6-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c20a6-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c20a6-129">Requirements</span></span>  
 <span data-ttu-id="c20a6-130">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c20a6-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c20a6-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="c20a6-131">See also</span></span>

- [<span data-ttu-id="c20a6-132">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="c20a6-132">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
