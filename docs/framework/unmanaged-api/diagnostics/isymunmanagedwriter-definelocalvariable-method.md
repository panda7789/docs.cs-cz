---
title: ISymUnmanagedWriter::DefineLocalVariable – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9466df3f6413f86eb8558f0037b96c254b2a2e1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777338"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a><span data-ttu-id="af8bd-102">ISymUnmanagedWriter::DefineLocalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="af8bd-102">ISymUnmanagedWriter::DefineLocalVariable Method</span></span>
<span data-ttu-id="af8bd-103">V aktuálním oboru lexikální definuje jednu proměnnou.</span><span class="sxs-lookup"><span data-stu-id="af8bd-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="af8bd-104">Tuto metodu lze volat pro proměnnou se stejným názvem, který má více domovů v rámci oboru více než jednou.</span><span class="sxs-lookup"><span data-stu-id="af8bd-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="af8bd-105">V takovém případě však hodnoty `startOffset` a `endOffset` parametry se nesmí překrývat.</span><span class="sxs-lookup"><span data-stu-id="af8bd-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af8bd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af8bd-106">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="af8bd-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="af8bd-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="af8bd-108">[in] Ukazatel `WCHAR` , který definuje název místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="af8bd-108">[in] A pointer to a `WCHAR` that defines the local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="af8bd-109">[in] Místní proměnné atributy.</span><span class="sxs-lookup"><span data-stu-id="af8bd-109">[in] The local variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="af8bd-110">[in] A `ULONG32` určující velikost v bajtech, nástroje `signature` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="af8bd-110">[in] A `ULONG32` that indicates the size, in bytes, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="af8bd-111">[in] Místní proměnné podpis.</span><span class="sxs-lookup"><span data-stu-id="af8bd-111">[in] The local variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="af8bd-112">[in] Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="af8bd-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="af8bd-113">[in] První adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="af8bd-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="af8bd-114">[in] Druhý adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="af8bd-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="af8bd-115">[in] Je třetí adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="af8bd-115">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="af8bd-116">[in] Počáteční odsazení pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="af8bd-116">[in] The start offset for the variable.</span></span> <span data-ttu-id="af8bd-117">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="af8bd-117">This parameter is optional.</span></span> <span data-ttu-id="af8bd-118">Pokud je 0, tento parametr je ignorován a proměnná je definována v rámci celého rozsahu.</span><span class="sxs-lookup"><span data-stu-id="af8bd-118">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="af8bd-119">Pokud je nenulovou hodnotu, proměnná spadá do posuny aktuálního oboru.</span><span class="sxs-lookup"><span data-stu-id="af8bd-119">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="af8bd-120">[in] Koncové odsazení pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="af8bd-120">[in] The end offset for the variable.</span></span> <span data-ttu-id="af8bd-121">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="af8bd-121">This parameter is optional.</span></span> <span data-ttu-id="af8bd-122">Pokud je 0, tento parametr je ignorován a proměnná je definována v rámci celého rozsahu.</span><span class="sxs-lookup"><span data-stu-id="af8bd-122">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="af8bd-123">Pokud je nenulovou hodnotu, proměnná spadá do posuny aktuálního oboru.</span><span class="sxs-lookup"><span data-stu-id="af8bd-123">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af8bd-124">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="af8bd-124">Return Value</span></span>  
 <span data-ttu-id="af8bd-125">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="af8bd-125">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af8bd-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af8bd-126">Requirements</span></span>  
 <span data-ttu-id="af8bd-127">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="af8bd-127">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af8bd-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af8bd-128">See also</span></span>

- [<span data-ttu-id="af8bd-129">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="af8bd-129">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="af8bd-130">DefineGlobalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="af8bd-130">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
- [<span data-ttu-id="af8bd-131">DefineLocalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="af8bd-131">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
