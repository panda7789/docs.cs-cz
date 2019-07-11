---
title: ISymUnmanagedVariable::GetSignature – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetSignature method [.NET Framework debugging]
ms.assetid: 78c1ba28-a410-4360-805c-23a95408964a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abd4bb00f5c1e703740462f1709407616ac8a8e8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778239"
---
# <a name="isymunmanagedvariablegetsignature-method"></a><span data-ttu-id="e7447-102">ISymUnmanagedVariable::GetSignature – metoda</span><span class="sxs-lookup"><span data-stu-id="e7447-102">ISymUnmanagedVariable::GetSignature Method</span></span>
<span data-ttu-id="e7447-103">Získá podpis této proměnné.</span><span class="sxs-lookup"><span data-stu-id="e7447-103">Gets the signature of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7447-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7447-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7447-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7447-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="e7447-106">[in] Délka vyrovnávací paměti na které odkazují `sig` parametru.</span><span class="sxs-lookup"><span data-stu-id="e7447-106">[in] The length of the buffer pointed to by the `sig` parameter.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="e7447-107">[out] Ukazatel `ULONG32` , která obdrží velikost ve znacích, vyrovnávací paměti musí obsahovat podpis.</span><span class="sxs-lookup"><span data-stu-id="e7447-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="e7447-108">[out] Vyrovnávací paměť, která ukládá podpis.</span><span class="sxs-lookup"><span data-stu-id="e7447-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7447-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e7447-109">Return Value</span></span>  
 <span data-ttu-id="e7447-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="e7447-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7447-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7447-111">Requirements</span></span>  
 <span data-ttu-id="e7447-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e7447-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7447-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7447-113">See also</span></span>

- [<span data-ttu-id="e7447-114">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e7447-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
