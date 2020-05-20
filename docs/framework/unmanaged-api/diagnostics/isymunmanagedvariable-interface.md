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
ms.openlocfilehash: d05d4451e8fb75829b22e0a1b9c9afcb0607eb8b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610168"
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="7c855-102">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c855-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="7c855-103">Představuje proměnnou, jako je například parametr, místní proměnná nebo pole.</span><span class="sxs-lookup"><span data-stu-id="7c855-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c855-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7c855-104">Methods</span></span>  
  
|<span data-ttu-id="7c855-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7c855-105">Method</span></span>|<span data-ttu-id="7c855-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7c855-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c855-107">GetAddressField1 – metoda</span><span class="sxs-lookup"><span data-stu-id="7c855-107">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="7c855-108">Získá první pole adresy pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="7c855-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="7c855-109">Jeho význam závisí na typu adresy.</span><span class="sxs-lookup"><span data-stu-id="7c855-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="7c855-110">GetAddressField2 – metoda</span><span class="sxs-lookup"><span data-stu-id="7c855-110">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="7c855-111">Získá druhé pole adresy pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="7c855-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="7c855-112">Jeho význam závisí na typu adresy.</span><span class="sxs-lookup"><span data-stu-id="7c855-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="7c855-113">GetAddressField3 – metoda</span><span class="sxs-lookup"><span data-stu-id="7c855-113">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="7c855-114">Získá třetí pole adresy pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="7c855-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="7c855-115">Jeho význam závisí na typu adresy.</span><span class="sxs-lookup"><span data-stu-id="7c855-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="7c855-116">GetAddressKind – metoda</span><span class="sxs-lookup"><span data-stu-id="7c855-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="7c855-117">Získá typ adresy této proměnné.</span><span class="sxs-lookup"><span data-stu-id="7c855-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="7c855-118">GetAttributes – metoda</span><span class="sxs-lookup"><span data-stu-id="7c855-118">GetAttributes Method</span></span>](isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="7c855-119">Získá příznaky atributu pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="7c855-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="7c855-120">GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="7c855-120">GetEndOffset Method</span></span>](isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="7c855-121">Získá koncový posun této proměnné v rámci své nadřazené položky.</span><span class="sxs-lookup"><span data-stu-id="7c855-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="7c855-122">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="7c855-122">GetName Method</span></span>](isymunmanagedvariable-getname-method.md)|<span data-ttu-id="7c855-123">Získá název této proměnné.</span><span class="sxs-lookup"><span data-stu-id="7c855-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="7c855-124">GetSignature – metoda</span><span class="sxs-lookup"><span data-stu-id="7c855-124">GetSignature Method</span></span>](isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="7c855-125">Načte podpis této proměnné.</span><span class="sxs-lookup"><span data-stu-id="7c855-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="7c855-126">GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="7c855-126">GetStartOffset Method</span></span>](isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="7c855-127">Získá počáteční posun této proměnné v rámci své nadřazené položky.</span><span class="sxs-lookup"><span data-stu-id="7c855-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7c855-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c855-128">Requirements</span></span>  
 <span data-ttu-id="7c855-129">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="7c855-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c855-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c855-130">See also</span></span>

- [<span data-ttu-id="7c855-131">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="7c855-131">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
