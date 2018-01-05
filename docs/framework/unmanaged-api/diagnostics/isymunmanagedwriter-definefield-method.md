---
title: "ISymUnmanagedWriter::DefineField – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineField
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51adddc6a8e58846ebefe3c130adaa670c8351e7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="1ce06-102">ISymUnmanagedWriter::DefineField – metoda</span><span class="sxs-lookup"><span data-stu-id="1ce06-102">ISymUnmanagedWriter::DefineField Method</span></span>
<span data-ttu-id="1ce06-103">Definuje samostatná proměnná, která není v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="1ce06-103">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="1ce06-104">Tato metoda je použít u některých polí v třídách, bitových polí a tak dále.</span><span class="sxs-lookup"><span data-stu-id="1ce06-104">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ce06-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ce06-105">Syntax</span></span>  
  
```  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ce06-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ce06-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="1ce06-107">[v] Metadata typ nebo metoda tokenu.</span><span class="sxs-lookup"><span data-stu-id="1ce06-107">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="1ce06-108">[v] Název pole.</span><span class="sxs-lookup"><span data-stu-id="1ce06-108">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="1ce06-109">[v] Atributy pole.</span><span class="sxs-lookup"><span data-stu-id="1ce06-109">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="1ce06-110">[v] A `ULONG32` to znamená velikost vyrovnávací paměti musí obsahovat pole podpis znakům.</span><span class="sxs-lookup"><span data-stu-id="1ce06-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="1ce06-111">[v] Pole podpisy pole.</span><span class="sxs-lookup"><span data-stu-id="1ce06-111">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="1ce06-112">[v] Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="1ce06-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="1ce06-113">[v] První adresa pro specifikaci pole.</span><span class="sxs-lookup"><span data-stu-id="1ce06-113">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="1ce06-114">[v] Druhý adresa pro specifikaci pole.</span><span class="sxs-lookup"><span data-stu-id="1ce06-114">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="1ce06-115">[v] Je třetí adresa pro specifikaci pole.</span><span class="sxs-lookup"><span data-stu-id="1ce06-115">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ce06-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1ce06-116">Return Value</span></span>  
 <span data-ttu-id="1ce06-117">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="1ce06-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ce06-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1ce06-118">Requirements</span></span>  
 <span data-ttu-id="1ce06-119">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1ce06-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ce06-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ce06-120">See Also</span></span>  
 [<span data-ttu-id="1ce06-121">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ce06-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
