---
title: "ISymUnmanagedVariable – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e5ae8d1d05274363dc523c1a2cebf4ed09c1f461
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="0ce0a-102">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ce0a-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="0ce0a-103">Představuje proměnnou, třeba parametr, místní proměnné nebo pole.</span><span class="sxs-lookup"><span data-stu-id="0ce0a-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ce0a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0ce0a-104">Methods</span></span>  
  
|<span data-ttu-id="0ce0a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0ce0a-105">Method</span></span>|<span data-ttu-id="0ce0a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0ce0a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ce0a-107">GetAddressField1 – metoda</span><span class="sxs-lookup"><span data-stu-id="0ce0a-107">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="0ce0a-108">Získá první pole adresy pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="0ce0a-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="0ce0a-109">Její význam závisí na druhu adresy.</span><span class="sxs-lookup"><span data-stu-id="0ce0a-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="0ce0a-110">GetAddressField2 – metoda</span><span class="sxs-lookup"><span data-stu-id="0ce0a-110">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="0ce0a-111">Získá druhý pole adresy pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="0ce0a-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="0ce0a-112">Její význam závisí na druhu adresy.</span><span class="sxs-lookup"><span data-stu-id="0ce0a-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="0ce0a-113">GetAddressField3 – metoda</span><span class="sxs-lookup"><span data-stu-id="0ce0a-113">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="0ce0a-114">Získá pole třetí adresa pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="0ce0a-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="0ce0a-115">Její význam závisí na druhu adresy.</span><span class="sxs-lookup"><span data-stu-id="0ce0a-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="0ce0a-116">GetAddressKind – metoda</span><span class="sxs-lookup"><span data-stu-id="0ce0a-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="0ce0a-117">Získá druh adresu tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="0ce0a-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="0ce0a-118">GetAttributes – metoda</span><span class="sxs-lookup"><span data-stu-id="0ce0a-118">GetAttributes Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="0ce0a-119">Získá atribut příznaků pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="0ce0a-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="0ce0a-120">GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="0ce0a-120">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="0ce0a-121">Získá posun end této proměnné v rámci jeho nadřazený objekt.</span><span class="sxs-lookup"><span data-stu-id="0ce0a-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="0ce0a-122">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="0ce0a-122">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|<span data-ttu-id="0ce0a-123">Získá název této proměnné.</span><span class="sxs-lookup"><span data-stu-id="0ce0a-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="0ce0a-124">GetSignature – metoda</span><span class="sxs-lookup"><span data-stu-id="0ce0a-124">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="0ce0a-125">Získá podpis tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="0ce0a-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="0ce0a-126">GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="0ce0a-126">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="0ce0a-127">Získá počáteční odsazení této proměnné v rámci jeho nadřazený objekt.</span><span class="sxs-lookup"><span data-stu-id="0ce0a-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0ce0a-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ce0a-128">Requirements</span></span>  
 <span data-ttu-id="0ce0a-129">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0ce0a-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ce0a-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ce0a-130">See Also</span></span>  
 [<span data-ttu-id="0ce0a-131">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="0ce0a-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
