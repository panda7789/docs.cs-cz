---
title: ISymUnmanagedWriter::DefineField – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5d5b3c60845fce39ce7f904c6871e7feb16e8970
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429811"
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="88ee4-102">ISymUnmanagedWriter::DefineField – metoda</span><span class="sxs-lookup"><span data-stu-id="88ee4-102">ISymUnmanagedWriter::DefineField Method</span></span>
<span data-ttu-id="88ee4-103">Definuje samostatná proměnná, která není v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="88ee4-103">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="88ee4-104">Tato metoda je použít u některých polí v třídách, bitových polí a tak dále.</span><span class="sxs-lookup"><span data-stu-id="88ee4-104">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88ee4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88ee4-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="88ee4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="88ee4-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="88ee4-107">[v] Metadata typ nebo metoda tokenu.</span><span class="sxs-lookup"><span data-stu-id="88ee4-107">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="88ee4-108">[v] Název pole.</span><span class="sxs-lookup"><span data-stu-id="88ee4-108">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="88ee4-109">[v] Atributy pole.</span><span class="sxs-lookup"><span data-stu-id="88ee4-109">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="88ee4-110">[v] A `ULONG32` to znamená velikost vyrovnávací paměti musí obsahovat pole podpis znakům.</span><span class="sxs-lookup"><span data-stu-id="88ee4-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="88ee4-111">[v] Pole podpisy pole.</span><span class="sxs-lookup"><span data-stu-id="88ee4-111">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="88ee4-112">[v] Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="88ee4-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="88ee4-113">[v] První adresa pro specifikaci pole.</span><span class="sxs-lookup"><span data-stu-id="88ee4-113">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="88ee4-114">[v] Druhý adresa pro specifikaci pole.</span><span class="sxs-lookup"><span data-stu-id="88ee4-114">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="88ee4-115">[v] Je třetí adresa pro specifikaci pole.</span><span class="sxs-lookup"><span data-stu-id="88ee4-115">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88ee4-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="88ee4-116">Return Value</span></span>  
 <span data-ttu-id="88ee4-117">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="88ee4-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88ee4-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="88ee4-118">Requirements</span></span>  
 <span data-ttu-id="88ee4-119">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="88ee4-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88ee4-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="88ee4-120">See Also</span></span>  
 [<span data-ttu-id="88ee4-121">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="88ee4-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
