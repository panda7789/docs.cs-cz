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
ms.openlocfilehash: 37794d40b4b379c5d3a05935cf1f2b7b3da11baa
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777361"
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="7cfa6-102">ISymUnmanagedWriter::DefineField – metoda</span><span class="sxs-lookup"><span data-stu-id="7cfa6-102">ISymUnmanagedWriter::DefineField Method</span></span>
<span data-ttu-id="7cfa6-103">Definuje jednu proměnnou, která není v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="7cfa6-103">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="7cfa6-104">Tato metoda je použité pro určité pole ve třídách, bitová pole a tak dále.</span><span class="sxs-lookup"><span data-stu-id="7cfa6-104">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cfa6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7cfa6-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="7cfa6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7cfa6-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="7cfa6-107">[in] Metadata typu nebo metodě tokenu.</span><span class="sxs-lookup"><span data-stu-id="7cfa6-107">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="7cfa6-108">[in] Název pole.</span><span class="sxs-lookup"><span data-stu-id="7cfa6-108">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="7cfa6-109">[in] Atributy pole.</span><span class="sxs-lookup"><span data-stu-id="7cfa6-109">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="7cfa6-110">[in] A `ULONG32` , který je velikost ve znacích, vyrovnávací paměti musí obsahovat podpis pole.</span><span class="sxs-lookup"><span data-stu-id="7cfa6-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="7cfa6-111">[in] Pole podpisy polí.</span><span class="sxs-lookup"><span data-stu-id="7cfa6-111">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="7cfa6-112">[in] Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="7cfa6-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="7cfa6-113">[in] První adresa specifikace pole.</span><span class="sxs-lookup"><span data-stu-id="7cfa6-113">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="7cfa6-114">[in] Druhý adresa specifikace pole.</span><span class="sxs-lookup"><span data-stu-id="7cfa6-114">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="7cfa6-115">[in] Je třetí adresa pro specifikaci pole.</span><span class="sxs-lookup"><span data-stu-id="7cfa6-115">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7cfa6-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7cfa6-116">Return Value</span></span>  
 <span data-ttu-id="7cfa6-117">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="7cfa6-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cfa6-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7cfa6-118">Requirements</span></span>  
 <span data-ttu-id="7cfa6-119">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7cfa6-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cfa6-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7cfa6-120">See also</span></span>

- [<span data-ttu-id="7cfa6-121">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7cfa6-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
