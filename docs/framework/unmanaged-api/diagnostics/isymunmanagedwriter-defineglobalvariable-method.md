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
ms.openlocfilehash: f1dd657c004c58480ea2f603ad4494753463c79b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428442"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="1a2c4-102">ISymUnmanagedWriter::DefineGlobalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="1a2c4-102">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>
<span data-ttu-id="1a2c4-103">Definuje jeden globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="1a2c4-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a2c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a2c4-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="1a2c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a2c4-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="1a2c4-106">[v] Ukazatel na `WCHAR` , který definuje název globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="1a2c4-106">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="1a2c4-107">[v] Globální proměnné atributy.</span><span class="sxs-lookup"><span data-stu-id="1a2c4-107">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="1a2c4-108">[v] A `ULONG32` určující velikost v znaků, z `signature` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1a2c4-108">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="1a2c4-109">[v] Globální proměnné podpis.</span><span class="sxs-lookup"><span data-stu-id="1a2c4-109">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="1a2c4-110">[v] Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="1a2c4-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="1a2c4-111">[v] První adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="1a2c4-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="1a2c4-112">[v] Druhý adresu pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="1a2c4-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="1a2c4-113">[v] Je třetí adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="1a2c4-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a2c4-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1a2c4-114">Return Value</span></span>  
 <span data-ttu-id="1a2c4-115">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="1a2c4-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a2c4-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1a2c4-116">Requirements</span></span>  
 <span data-ttu-id="1a2c4-117">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1a2c4-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a2c4-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a2c4-118">See Also</span></span>  
 [<span data-ttu-id="1a2c4-119">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1a2c4-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="1a2c4-120">DefineLocalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="1a2c4-120">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)  
 [<span data-ttu-id="1a2c4-121">DefineGlobalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="1a2c4-121">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)
