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
ms.openlocfilehash: 0c7cf800dafa9f3e213a012f49c73d51c78e7074
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427402"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="3299c-102">ISymUnmanagedWriter::DefineConstant – metoda</span><span class="sxs-lookup"><span data-stu-id="3299c-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="3299c-103">Definuje název pro konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3299c-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3299c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3299c-104">Syntax</span></span>  
  
```  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3299c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3299c-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="3299c-106">[v] Ukazatel na `WCHAR` , který definuje název konstantní.</span><span class="sxs-lookup"><span data-stu-id="3299c-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="3299c-107">[v] Hodnota konstanty.</span><span class="sxs-lookup"><span data-stu-id="3299c-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="3299c-108">[v] Velikost `signature` pole.</span><span class="sxs-lookup"><span data-stu-id="3299c-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="3299c-109">[v] Typ podpis pro konstanta.</span><span class="sxs-lookup"><span data-stu-id="3299c-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3299c-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3299c-110">Return Value</span></span>  
 <span data-ttu-id="3299c-111">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="3299c-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3299c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3299c-112">Requirements</span></span>  
 <span data-ttu-id="3299c-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3299c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3299c-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="3299c-114">See Also</span></span>  
 [<span data-ttu-id="3299c-115">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3299c-115">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="3299c-116">DefineConstant2 – metoda</span><span class="sxs-lookup"><span data-stu-id="3299c-116">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)
