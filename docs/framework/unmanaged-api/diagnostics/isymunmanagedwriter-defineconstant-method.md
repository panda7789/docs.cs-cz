---
title: ISymUnmanagedWriter::DefineConstant – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineConstant
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineConstant
helpviewer_keywords:
- DefineConstant method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineConstant method [.NET Framework debugging]
ms.assetid: 9e986986-2223-4d5f-b040-85d716146924
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f470dbe4ef2ef0d5f2204ccbdd5fb64730f9a2c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159754"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="6eaff-102">ISymUnmanagedWriter::DefineConstant – metoda</span><span class="sxs-lookup"><span data-stu-id="6eaff-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="6eaff-103">Definuje název pro konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6eaff-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eaff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6eaff-104">Syntax</span></span>  
  
```  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6eaff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6eaff-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="6eaff-106">[in] Ukazatel `WCHAR` , který definuje název konstantní.</span><span class="sxs-lookup"><span data-stu-id="6eaff-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="6eaff-107">[in] Hodnota konstanty.</span><span class="sxs-lookup"><span data-stu-id="6eaff-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="6eaff-108">[in] Velikost `signature` pole.</span><span class="sxs-lookup"><span data-stu-id="6eaff-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="6eaff-109">[in] Podpis typu pro konstantu.</span><span class="sxs-lookup"><span data-stu-id="6eaff-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6eaff-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6eaff-110">Return Value</span></span>  
 <span data-ttu-id="6eaff-111">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="6eaff-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eaff-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6eaff-112">Requirements</span></span>  
 <span data-ttu-id="6eaff-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6eaff-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eaff-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6eaff-114">See also</span></span>

- [<span data-ttu-id="6eaff-115">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6eaff-115">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="6eaff-116">DefineConstant2 – metoda</span><span class="sxs-lookup"><span data-stu-id="6eaff-116">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)
