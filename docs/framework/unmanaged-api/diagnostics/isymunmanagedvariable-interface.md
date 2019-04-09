---
title: ISymUnmanagedVariable – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable
helpviewer_keywords:
- ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 712eca7f3f9fec9c81e638802f5a664ec6469d53
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164343"
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="e0877-102">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e0877-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="e0877-103">Představuje proměnnou, jako je například parametr, místní proměnné nebo pole.</span><span class="sxs-lookup"><span data-stu-id="e0877-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e0877-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e0877-104">Methods</span></span>  
  
|<span data-ttu-id="e0877-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e0877-105">Method</span></span>|<span data-ttu-id="e0877-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e0877-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e0877-107">GetAddressField1 – metoda</span><span class="sxs-lookup"><span data-stu-id="e0877-107">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="e0877-108">Získá první pole adresy pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="e0877-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="e0877-109">Její význam závisí na druhu adresu.</span><span class="sxs-lookup"><span data-stu-id="e0877-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="e0877-110">GetAddressField2 – metoda</span><span class="sxs-lookup"><span data-stu-id="e0877-110">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="e0877-111">Získá druhý pole adresy pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="e0877-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="e0877-112">Její význam závisí na druhu adresu.</span><span class="sxs-lookup"><span data-stu-id="e0877-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="e0877-113">GetAddressField3 – metoda</span><span class="sxs-lookup"><span data-stu-id="e0877-113">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="e0877-114">Získá pole třetí adresa pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="e0877-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="e0877-115">Její význam závisí na druhu adresu.</span><span class="sxs-lookup"><span data-stu-id="e0877-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="e0877-116">GetAddressKind – metoda</span><span class="sxs-lookup"><span data-stu-id="e0877-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="e0877-117">Získá druh adresu této proměnné.</span><span class="sxs-lookup"><span data-stu-id="e0877-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="e0877-118">GetAttributes – metoda</span><span class="sxs-lookup"><span data-stu-id="e0877-118">GetAttributes Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="e0877-119">Získá příznaky atributu pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="e0877-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="e0877-120">GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="e0877-120">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="e0877-121">Získá posun ukončení této proměnné v rámci svého nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="e0877-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="e0877-122">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="e0877-122">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|<span data-ttu-id="e0877-123">Získá název této proměnné.</span><span class="sxs-lookup"><span data-stu-id="e0877-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="e0877-124">GetSignature – metoda</span><span class="sxs-lookup"><span data-stu-id="e0877-124">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="e0877-125">Získá podpis této proměnné.</span><span class="sxs-lookup"><span data-stu-id="e0877-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="e0877-126">GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="e0877-126">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="e0877-127">Získá počáteční odsazení této proměnné v rámci svého nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="e0877-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e0877-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0877-128">Requirements</span></span>  
 <span data-ttu-id="e0877-129">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e0877-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0877-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0877-130">See also</span></span>

- [<span data-ttu-id="e0877-131">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="e0877-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
