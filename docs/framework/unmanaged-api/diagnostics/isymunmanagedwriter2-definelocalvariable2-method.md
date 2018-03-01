---
title: "ISymUnmanagedWriter2::DefineLocalVariable2 – metoda"
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
- ISymUnmanagedWriter2.DefineLocalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1124b57bed16e349c753be872c1b709a287e6237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="c7db7-102">ISymUnmanagedWriter2::DefineLocalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="c7db7-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>
<span data-ttu-id="c7db7-103">V aktuálním oboru lexikální definuje jednu proměnnou.</span><span class="sxs-lookup"><span data-stu-id="c7db7-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="c7db7-104">Tuto metodu lze volat vícekrát proměnné se stejným názvem, který má více domácnostech v rámci oboru.</span><span class="sxs-lookup"><span data-stu-id="c7db7-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="c7db7-105">V takovém případě však hodnoty `startOffset` a `endOffset` parametry se nesmí překrývat.</span><span class="sxs-lookup"><span data-stu-id="c7db7-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7db7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7db7-106">Syntax</span></span>  
  
```  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7db7-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7db7-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="c7db7-108">[v] Místní název proměnné.</span><span class="sxs-lookup"><span data-stu-id="c7db7-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="c7db7-109">[v] Místní proměnné atributy.</span><span class="sxs-lookup"><span data-stu-id="c7db7-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="c7db7-110">[v] Podpis tokenu metadat.</span><span class="sxs-lookup"><span data-stu-id="c7db7-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="c7db7-111">[v] Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="c7db7-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="c7db7-112">[v] První adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="c7db7-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="c7db7-113">[v] Druhý adresu pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="c7db7-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="c7db7-114">[v] Je třetí adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="c7db7-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="c7db7-115">[v] Počáteční odsazení proměnné.</span><span class="sxs-lookup"><span data-stu-id="c7db7-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="c7db7-116">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="c7db7-116">This parameter is optional.</span></span> <span data-ttu-id="c7db7-117">Pokud je 0, tento parametr je ignorován a proměnná je definována v rámci celého rozsahu.</span><span class="sxs-lookup"><span data-stu-id="c7db7-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="c7db7-118">Pokud je nenulovou hodnotu, proměnná spadá do posunutí aktuálního oboru.</span><span class="sxs-lookup"><span data-stu-id="c7db7-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="c7db7-119">[v] Koncové posunutí pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="c7db7-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="c7db7-120">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="c7db7-120">This parameter is optional.</span></span> <span data-ttu-id="c7db7-121">Pokud je 0, tento parametr je ignorován a proměnná je definována v rámci celého rozsahu.</span><span class="sxs-lookup"><span data-stu-id="c7db7-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="c7db7-122">Pokud je nenulovou hodnotu, proměnná spadá do posunutí aktuálního oboru.</span><span class="sxs-lookup"><span data-stu-id="c7db7-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7db7-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c7db7-123">Return Value</span></span>  
 <span data-ttu-id="c7db7-124">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="c7db7-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7db7-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7db7-125">Requirements</span></span>  
 <span data-ttu-id="c7db7-126">**Záhlaví:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="c7db7-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7db7-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7db7-127">See Also</span></span>  
 [<span data-ttu-id="c7db7-128">ISymUnmanagedWriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c7db7-128">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [<span data-ttu-id="c7db7-129">DefineLocalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="c7db7-129">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
