---
title: "ISymUnmanagedVariable::GetSignature – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetSignature
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetSignature method [.NET Framework debugging]
ms.assetid: 78c1ba28-a410-4360-805c-23a95408964a
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1e29cd4a38e9abbe380b51b81fc2849b833d87e9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedvariablegetsignature-method"></a><span data-ttu-id="05eb0-102">ISymUnmanagedVariable::GetSignature – metoda</span><span class="sxs-lookup"><span data-stu-id="05eb0-102">ISymUnmanagedVariable::GetSignature Method</span></span>
<span data-ttu-id="05eb0-103">Získá podpis tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="05eb0-103">Gets the signature of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05eb0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05eb0-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05eb0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05eb0-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="05eb0-106">[v] Délka vyrovnávací paměti na kterou odkazuje `sig` parametr.</span><span class="sxs-lookup"><span data-stu-id="05eb0-106">[in] The length of the buffer pointed to by the `sig` parameter.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="05eb0-107">[out] Ukazatel na `ULONG32` velikostí, která přijme ve znacích vyrovnávací paměti musí obsahovat podpis.</span><span class="sxs-lookup"><span data-stu-id="05eb0-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="05eb0-108">[out] Vyrovnávací paměť, která ukládá podpis.</span><span class="sxs-lookup"><span data-stu-id="05eb0-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05eb0-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="05eb0-109">Return Value</span></span>  
 <span data-ttu-id="05eb0-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="05eb0-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05eb0-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05eb0-111">Requirements</span></span>  
 <span data-ttu-id="05eb0-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="05eb0-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05eb0-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="05eb0-113">See Also</span></span>  
 [<span data-ttu-id="05eb0-114">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05eb0-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
