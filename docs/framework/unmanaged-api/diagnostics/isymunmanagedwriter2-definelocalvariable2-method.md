---
title: ISymUnmanagedWriter2::DefineLocalVariable2 – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8fa385805d3e2dca8fef3e1490b2c67dd0583373
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755063"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="00a88-102">ISymUnmanagedWriter2::DefineLocalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="00a88-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>
<span data-ttu-id="00a88-103">V aktuálním oboru lexikální definuje jednu proměnnou.</span><span class="sxs-lookup"><span data-stu-id="00a88-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="00a88-104">Tuto metodu lze volat pro proměnnou se stejným názvem, který má více domovů v rámci oboru více než jednou.</span><span class="sxs-lookup"><span data-stu-id="00a88-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="00a88-105">V takovém případě však hodnoty `startOffset` a `endOffset` parametry se nesmí překrývat.</span><span class="sxs-lookup"><span data-stu-id="00a88-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00a88-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00a88-106">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="00a88-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="00a88-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="00a88-108">[in] Název místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="00a88-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="00a88-109">[in] Místní proměnné atributy.</span><span class="sxs-lookup"><span data-stu-id="00a88-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="00a88-110">[in] Metadata token podpisu.</span><span class="sxs-lookup"><span data-stu-id="00a88-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="00a88-111">[in] Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="00a88-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="00a88-112">[in] První adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="00a88-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="00a88-113">[in] Druhý adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="00a88-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="00a88-114">[in] Je třetí adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="00a88-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="00a88-115">[in] Počáteční odsazení pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="00a88-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="00a88-116">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="00a88-116">This parameter is optional.</span></span> <span data-ttu-id="00a88-117">Pokud je 0, tento parametr je ignorován a proměnná je definována v rámci celého rozsahu.</span><span class="sxs-lookup"><span data-stu-id="00a88-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="00a88-118">Pokud je nenulovou hodnotu, proměnná spadá do posuny aktuálního oboru.</span><span class="sxs-lookup"><span data-stu-id="00a88-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="00a88-119">[in] Koncové odsazení pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="00a88-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="00a88-120">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="00a88-120">This parameter is optional.</span></span> <span data-ttu-id="00a88-121">Pokud je 0, tento parametr je ignorován a proměnná je definována v rámci celého rozsahu.</span><span class="sxs-lookup"><span data-stu-id="00a88-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="00a88-122">Pokud je nenulovou hodnotu, proměnná spadá do posuny aktuálního oboru.</span><span class="sxs-lookup"><span data-stu-id="00a88-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00a88-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="00a88-123">Return Value</span></span>  
 <span data-ttu-id="00a88-124">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="00a88-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00a88-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00a88-125">Requirements</span></span>  
 <span data-ttu-id="00a88-126">**Záhlaví:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="00a88-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00a88-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00a88-127">See also</span></span>

- [<span data-ttu-id="00a88-128">ISymUnmanagedWriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00a88-128">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="00a88-129">DefineLocalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="00a88-129">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
