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
ms.openlocfilehash: ee57ba14f048032e2cd9d0129089743c0f0304bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445985"
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="140f1-102">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="140f1-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="140f1-103">Představuje proměnnou, jako je například parametr, místní proměnná nebo pole.</span><span class="sxs-lookup"><span data-stu-id="140f1-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="140f1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="140f1-104">Methods</span></span>  
  
|<span data-ttu-id="140f1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="140f1-105">Method</span></span>|<span data-ttu-id="140f1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="140f1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="140f1-107">GetAddressField1 – metoda</span><span class="sxs-lookup"><span data-stu-id="140f1-107">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="140f1-108">Získá první pole adresy pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="140f1-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="140f1-109">Jeho význam závisí na typu adresy.</span><span class="sxs-lookup"><span data-stu-id="140f1-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="140f1-110">GetAddressField2 – metoda</span><span class="sxs-lookup"><span data-stu-id="140f1-110">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="140f1-111">Získá druhé pole adresy pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="140f1-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="140f1-112">Jeho význam závisí na typu adresy.</span><span class="sxs-lookup"><span data-stu-id="140f1-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="140f1-113">GetAddressField3 – metoda</span><span class="sxs-lookup"><span data-stu-id="140f1-113">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="140f1-114">Získá třetí pole adresy pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="140f1-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="140f1-115">Jeho význam závisí na typu adresy.</span><span class="sxs-lookup"><span data-stu-id="140f1-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="140f1-116">GetAddressKind – metoda</span><span class="sxs-lookup"><span data-stu-id="140f1-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="140f1-117">Získá typ adresy této proměnné.</span><span class="sxs-lookup"><span data-stu-id="140f1-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="140f1-118">GetAttributes – metoda</span><span class="sxs-lookup"><span data-stu-id="140f1-118">GetAttributes Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="140f1-119">Získá příznaky atributu pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="140f1-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="140f1-120">GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="140f1-120">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="140f1-121">Získá koncový posun této proměnné v rámci své nadřazené položky.</span><span class="sxs-lookup"><span data-stu-id="140f1-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="140f1-122">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="140f1-122">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|<span data-ttu-id="140f1-123">Získá název této proměnné.</span><span class="sxs-lookup"><span data-stu-id="140f1-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="140f1-124">GetSignature – metoda</span><span class="sxs-lookup"><span data-stu-id="140f1-124">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="140f1-125">Načte podpis této proměnné.</span><span class="sxs-lookup"><span data-stu-id="140f1-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="140f1-126">GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="140f1-126">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="140f1-127">Získá počáteční posun této proměnné v rámci své nadřazené položky.</span><span class="sxs-lookup"><span data-stu-id="140f1-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="140f1-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="140f1-128">Requirements</span></span>  
 <span data-ttu-id="140f1-129">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="140f1-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="140f1-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="140f1-130">See also</span></span>

- [<span data-ttu-id="140f1-131">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="140f1-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
