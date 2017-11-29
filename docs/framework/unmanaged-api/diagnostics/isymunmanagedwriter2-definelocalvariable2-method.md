---
title: "ISymUnmanagedWriter2::DefineLocalVariable2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter2.DefineLocalVariable2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 595cc3d8c503a5a6b2cbcb6665f7ff8aff5044d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="a27ba-102">ISymUnmanagedWriter2::DefineLocalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="a27ba-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>
<span data-ttu-id="a27ba-103">V aktuálním oboru lexikální definuje jednu proměnnou.</span><span class="sxs-lookup"><span data-stu-id="a27ba-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="a27ba-104">Tuto metodu lze volat vícekrát proměnné se stejným názvem, který má více domácnostech v rámci oboru.</span><span class="sxs-lookup"><span data-stu-id="a27ba-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="a27ba-105">V takovém případě však hodnoty `startOffset` a `endOffset` parametry se nesmí překrývat.</span><span class="sxs-lookup"><span data-stu-id="a27ba-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a27ba-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a27ba-106">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="a27ba-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a27ba-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="a27ba-108">[v] Místní název proměnné.</span><span class="sxs-lookup"><span data-stu-id="a27ba-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="a27ba-109">[v] Místní proměnné atributy.</span><span class="sxs-lookup"><span data-stu-id="a27ba-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="a27ba-110">[v] Podpis tokenu metadat.</span><span class="sxs-lookup"><span data-stu-id="a27ba-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="a27ba-111">[v] Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="a27ba-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="a27ba-112">[v] První adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="a27ba-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="a27ba-113">[v] Druhý adresu pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="a27ba-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="a27ba-114">[v] Je třetí adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="a27ba-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="a27ba-115">[v] Počáteční odsazení proměnné.</span><span class="sxs-lookup"><span data-stu-id="a27ba-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="a27ba-116">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="a27ba-116">This parameter is optional.</span></span> <span data-ttu-id="a27ba-117">Pokud je 0, tento parametr je ignorován a proměnná je definována v rámci celého rozsahu.</span><span class="sxs-lookup"><span data-stu-id="a27ba-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="a27ba-118">Pokud je nenulovou hodnotu, proměnná spadá do posunutí aktuálního oboru.</span><span class="sxs-lookup"><span data-stu-id="a27ba-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="a27ba-119">[v] Koncové posunutí pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="a27ba-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="a27ba-120">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="a27ba-120">This parameter is optional.</span></span> <span data-ttu-id="a27ba-121">Pokud je 0, tento parametr je ignorován a proměnná je definována v rámci celého rozsahu.</span><span class="sxs-lookup"><span data-stu-id="a27ba-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="a27ba-122">Pokud je nenulovou hodnotu, proměnná spadá do posunutí aktuálního oboru.</span><span class="sxs-lookup"><span data-stu-id="a27ba-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a27ba-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a27ba-123">Return Value</span></span>  
 <span data-ttu-id="a27ba-124">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="a27ba-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a27ba-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a27ba-125">Requirements</span></span>  
 <span data-ttu-id="a27ba-126">**Záhlaví:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="a27ba-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a27ba-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="a27ba-127">See Also</span></span>  
 [<span data-ttu-id="a27ba-128">Isymunmanagedwriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a27ba-128">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [<span data-ttu-id="a27ba-129">Definelocalvariable – metoda</span><span class="sxs-lookup"><span data-stu-id="a27ba-129">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
