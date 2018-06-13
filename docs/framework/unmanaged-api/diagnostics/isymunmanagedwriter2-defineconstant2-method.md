---
title: ISymUnmanagedWriter2::DefineConstant2 – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineConstant2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineConstant2
helpviewer_keywords:
- DefineConstant2 method [.NET Framework debugging]
- ISymUnmanagedWriter2::DefineConstant2 method [.NET Framework debugging]
ms.assetid: dd2bc956-7dbe-49fc-a646-daa0d267f2df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c6f9f198fc1115aed7b531515ab07ddc35d36ba8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427333"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="23d41-102">ISymUnmanagedWriter2::DefineConstant2 – metoda</span><span class="sxs-lookup"><span data-stu-id="23d41-102">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>
<span data-ttu-id="23d41-103">Definuje název pro konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="23d41-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23d41-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23d41-104">Syntax</span></span>  
  
```  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23d41-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="23d41-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="23d41-106">[v] Název konstantní.</span><span class="sxs-lookup"><span data-stu-id="23d41-106">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="23d41-107">[v] Hodnota konstanty.</span><span class="sxs-lookup"><span data-stu-id="23d41-107">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="23d41-108">[v] Metadata token konstanty.</span><span class="sxs-lookup"><span data-stu-id="23d41-108">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23d41-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="23d41-109">Return Value</span></span>  
 <span data-ttu-id="23d41-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="23d41-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23d41-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="23d41-111">Requirements</span></span>  
 <span data-ttu-id="23d41-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="23d41-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23d41-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="23d41-113">See Also</span></span>  
 [<span data-ttu-id="23d41-114">ISymUnmanagedWriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="23d41-114">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [<span data-ttu-id="23d41-115">DefineConstant – metoda</span><span class="sxs-lookup"><span data-stu-id="23d41-115">DefineConstant Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)
