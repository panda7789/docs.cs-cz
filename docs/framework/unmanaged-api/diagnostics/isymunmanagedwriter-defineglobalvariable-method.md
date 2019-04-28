---
title: ISymUnmanagedWriter::DefineGlobalVariable – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineGlobalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66efe5ae1fe2154684d2ac6791895b7fcbe4f7b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763585"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="ba64a-102">ISymUnmanagedWriter::DefineGlobalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="ba64a-102">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>
<span data-ttu-id="ba64a-103">Definuje jeden globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="ba64a-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba64a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba64a-104">Syntax</span></span>  
  
```  
HRESULT DefineGlobalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba64a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba64a-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="ba64a-106">[in] Ukazatel `WCHAR` , který definuje název globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="ba64a-106">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="ba64a-107">[in] Globální proměnné atributy.</span><span class="sxs-lookup"><span data-stu-id="ba64a-107">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="ba64a-108">[in] A `ULONG32` , který označuje velikost ve znacích, nástroje `signature` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ba64a-108">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="ba64a-109">[in] Globální proměnné podpis.</span><span class="sxs-lookup"><span data-stu-id="ba64a-109">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="ba64a-110">[in] Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="ba64a-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="ba64a-111">[in] První adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="ba64a-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="ba64a-112">[in] Druhý adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="ba64a-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="ba64a-113">[in] Je třetí adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="ba64a-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba64a-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ba64a-114">Return Value</span></span>  
 <span data-ttu-id="ba64a-115">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="ba64a-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba64a-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba64a-116">Requirements</span></span>  
 <span data-ttu-id="ba64a-117">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ba64a-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba64a-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba64a-118">See also</span></span>

- [<span data-ttu-id="ba64a-119">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba64a-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="ba64a-120">DefineLocalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="ba64a-120">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
- [<span data-ttu-id="ba64a-121">DefineGlobalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="ba64a-121">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)
