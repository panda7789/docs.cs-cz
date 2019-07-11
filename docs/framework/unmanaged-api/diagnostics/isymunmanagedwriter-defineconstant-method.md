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
ms.openlocfilehash: a04bf93a2b2809198673d15f29714f52c9435b68
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767837"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="aaaea-102">ISymUnmanagedWriter::DefineConstant – metoda</span><span class="sxs-lookup"><span data-stu-id="aaaea-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="aaaea-103">Definuje název pro konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="aaaea-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaaea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aaaea-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aaaea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aaaea-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="aaaea-106">[in] Ukazatel `WCHAR` , který definuje název konstantní.</span><span class="sxs-lookup"><span data-stu-id="aaaea-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="aaaea-107">[in] Hodnota konstanty.</span><span class="sxs-lookup"><span data-stu-id="aaaea-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="aaaea-108">[in] Velikost `signature` pole.</span><span class="sxs-lookup"><span data-stu-id="aaaea-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="aaaea-109">[in] Podpis typu pro konstantu.</span><span class="sxs-lookup"><span data-stu-id="aaaea-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aaaea-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aaaea-110">Return Value</span></span>  
 <span data-ttu-id="aaaea-111">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="aaaea-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaaea-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aaaea-112">Requirements</span></span>  
 <span data-ttu-id="aaaea-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="aaaea-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaaea-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aaaea-114">See also</span></span>

- [<span data-ttu-id="aaaea-115">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aaaea-115">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="aaaea-116">DefineConstant2 – metoda</span><span class="sxs-lookup"><span data-stu-id="aaaea-116">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)
