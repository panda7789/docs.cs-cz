---
title: "ISymUnmanagedConstant::GetSignature – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedConstant.GetSignature
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedConstant::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetSignature method [.NET Framework debugging]
ms.assetid: 3eb41151-a228-43e3-ba8f-e6dd3ceb8542
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 314d9115fdba7d57538e5b24c56863944db517fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="b58ac-102">ISymUnmanagedConstant::GetSignature – metoda</span><span class="sxs-lookup"><span data-stu-id="b58ac-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="b58ac-103">Získá podpis konstanty.</span><span class="sxs-lookup"><span data-stu-id="b58ac-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b58ac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b58ac-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b58ac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b58ac-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="b58ac-106">[v] Délka vyrovnávací paměti, která `pcSig` parametr odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="b58ac-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="b58ac-107">[out] Ukazatel na `ULONG32` velikostí, která přijme ve znacích vyrovnávací paměti musí obsahovat podpis.</span><span class="sxs-lookup"><span data-stu-id="b58ac-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="b58ac-108">[out] Vyrovnávací paměť, která ukládá podpis.</span><span class="sxs-lookup"><span data-stu-id="b58ac-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b58ac-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b58ac-109">Return Value</span></span>  
 <span data-ttu-id="b58ac-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="b58ac-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b58ac-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b58ac-111">Requirements</span></span>  
 <span data-ttu-id="b58ac-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b58ac-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b58ac-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="b58ac-113">See Also</span></span>  
 [<span data-ttu-id="b58ac-114">ISymUnmanagedConstant – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="b58ac-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="b58ac-115">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="b58ac-115">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)  
 [<span data-ttu-id="b58ac-116">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="b58ac-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
