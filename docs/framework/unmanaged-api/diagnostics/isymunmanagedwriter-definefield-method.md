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
ms.openlocfilehash: 5fd9798b3681d66e71d5703f4d16564b153da07b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176173"
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="94bcc-102">ISymUnmanagedWriter::DefineField – metoda</span><span class="sxs-lookup"><span data-stu-id="94bcc-102">ISymUnmanagedWriter::DefineField Method</span></span>
<span data-ttu-id="94bcc-103">Definuje jednu proměnnou, která není v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="94bcc-103">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="94bcc-104">Tato metoda je použité pro určité pole ve třídách, bitová pole a tak dále.</span><span class="sxs-lookup"><span data-stu-id="94bcc-104">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94bcc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94bcc-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="94bcc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="94bcc-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="94bcc-107">[in] Metadata typu nebo metodě tokenu.</span><span class="sxs-lookup"><span data-stu-id="94bcc-107">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="94bcc-108">[in] Název pole.</span><span class="sxs-lookup"><span data-stu-id="94bcc-108">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="94bcc-109">[in] Atributy pole.</span><span class="sxs-lookup"><span data-stu-id="94bcc-109">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="94bcc-110">[in] A `ULONG32` , který je velikost ve znacích, vyrovnávací paměti musí obsahovat podpis pole.</span><span class="sxs-lookup"><span data-stu-id="94bcc-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="94bcc-111">[in] Pole podpisy polí.</span><span class="sxs-lookup"><span data-stu-id="94bcc-111">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="94bcc-112">[in] Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="94bcc-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="94bcc-113">[in] První adresa specifikace pole.</span><span class="sxs-lookup"><span data-stu-id="94bcc-113">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="94bcc-114">[in] Druhý adresa specifikace pole.</span><span class="sxs-lookup"><span data-stu-id="94bcc-114">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="94bcc-115">[in] Je třetí adresa pro specifikaci pole.</span><span class="sxs-lookup"><span data-stu-id="94bcc-115">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94bcc-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="94bcc-116">Return Value</span></span>  
 <span data-ttu-id="94bcc-117">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="94bcc-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94bcc-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="94bcc-118">Requirements</span></span>  
 <span data-ttu-id="94bcc-119">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="94bcc-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94bcc-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94bcc-120">See also</span></span>

- [<span data-ttu-id="94bcc-121">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="94bcc-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
