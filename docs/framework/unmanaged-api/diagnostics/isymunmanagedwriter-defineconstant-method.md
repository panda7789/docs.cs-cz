---
title: "ISymUnmanagedWriter::DefineConstant – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineConstant
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineConstant
helpviewer_keywords:
- DefineConstant method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineConstant method [.NET Framework debugging]
ms.assetid: 9e986986-2223-4d5f-b040-85d716146924
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 910f2e753849b955a398f2175342b2f94849fba6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="2a031-102">ISymUnmanagedWriter::DefineConstant – metoda</span><span class="sxs-lookup"><span data-stu-id="2a031-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="2a031-103">Definuje název pro konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2a031-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a031-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a031-104">Syntax</span></span>  
  
```  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a031-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a031-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="2a031-106">[v] Ukazatel na `WCHAR` , který definuje název konstantní.</span><span class="sxs-lookup"><span data-stu-id="2a031-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="2a031-107">[v] Hodnota konstanty.</span><span class="sxs-lookup"><span data-stu-id="2a031-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="2a031-108">[v] Velikost `signature` pole.</span><span class="sxs-lookup"><span data-stu-id="2a031-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="2a031-109">[v] Typ podpis pro konstanta.</span><span class="sxs-lookup"><span data-stu-id="2a031-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a031-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2a031-110">Return Value</span></span>  
 <span data-ttu-id="2a031-111">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="2a031-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a031-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2a031-112">Requirements</span></span>  
 <span data-ttu-id="2a031-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2a031-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a031-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a031-114">See Also</span></span>  
 [<span data-ttu-id="2a031-115">ISymUnmanagedWriter – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="2a031-115">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="2a031-116">Defineconstant2 – metoda</span><span class="sxs-lookup"><span data-stu-id="2a031-116">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)
