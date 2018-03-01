---
title: "ISymUnmanagedWriter::DefineLocalVariable – metoda"
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
- ISymUnmanagedWriter.DefineLocalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 89ea3e23166b4745b34b7c2af498d29564cdd68d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a><span data-ttu-id="03d93-102">ISymUnmanagedWriter::DefineLocalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="03d93-102">ISymUnmanagedWriter::DefineLocalVariable Method</span></span>
<span data-ttu-id="03d93-103">V aktuálním oboru lexikální definuje jednu proměnnou.</span><span class="sxs-lookup"><span data-stu-id="03d93-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="03d93-104">Tuto metodu lze volat vícekrát proměnné se stejným názvem, který má více domácnostech v rámci oboru.</span><span class="sxs-lookup"><span data-stu-id="03d93-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="03d93-105">V takovém případě však hodnoty `startOffset` a `endOffset` parametry se nesmí překrývat.</span><span class="sxs-lookup"><span data-stu-id="03d93-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03d93-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03d93-106">Syntax</span></span>  
  
```  
HRESULT DefineLocalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03d93-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="03d93-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="03d93-108">[v] Ukazatel na `WCHAR` , který definuje místní název proměnné.</span><span class="sxs-lookup"><span data-stu-id="03d93-108">[in] A pointer to a `WCHAR` that defines the local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="03d93-109">[v] Místní proměnné atributy.</span><span class="sxs-lookup"><span data-stu-id="03d93-109">[in] The local variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="03d93-110">[v] A `ULONG32` určující velikost v bajtech z `signature` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="03d93-110">[in] A `ULONG32` that indicates the size, in bytes, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="03d93-111">[v] Místní proměnné podpis.</span><span class="sxs-lookup"><span data-stu-id="03d93-111">[in] The local variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="03d93-112">[v] Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="03d93-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="03d93-113">[v] První adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="03d93-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="03d93-114">[v] Druhý adresu pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="03d93-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="03d93-115">[v] Je třetí adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="03d93-115">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="03d93-116">[v] Počáteční odsazení proměnné.</span><span class="sxs-lookup"><span data-stu-id="03d93-116">[in] The start offset for the variable.</span></span> <span data-ttu-id="03d93-117">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="03d93-117">This parameter is optional.</span></span> <span data-ttu-id="03d93-118">Pokud je 0, tento parametr je ignorován a proměnná je definována v rámci celého rozsahu.</span><span class="sxs-lookup"><span data-stu-id="03d93-118">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="03d93-119">Pokud je nenulovou hodnotu, proměnná spadá do posunutí aktuálního oboru.</span><span class="sxs-lookup"><span data-stu-id="03d93-119">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="03d93-120">[v] Koncové posunutí pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="03d93-120">[in] The end offset for the variable.</span></span> <span data-ttu-id="03d93-121">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="03d93-121">This parameter is optional.</span></span> <span data-ttu-id="03d93-122">Pokud je 0, tento parametr je ignorován a proměnná je definována v rámci celého rozsahu.</span><span class="sxs-lookup"><span data-stu-id="03d93-122">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="03d93-123">Pokud je nenulovou hodnotu, proměnná spadá do posunutí aktuálního oboru.</span><span class="sxs-lookup"><span data-stu-id="03d93-123">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03d93-124">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="03d93-124">Return Value</span></span>  
 <span data-ttu-id="03d93-125">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="03d93-125">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03d93-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03d93-126">Requirements</span></span>  
 <span data-ttu-id="03d93-127">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="03d93-127">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03d93-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="03d93-128">See Also</span></span>  
 [<span data-ttu-id="03d93-129">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="03d93-129">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="03d93-130">DefineGlobalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="03d93-130">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)  
 [<span data-ttu-id="03d93-131">DefineLocalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="03d93-131">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
