---
title: ISymUnmanagedConstant::GetSignature – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetSignature method [.NET Framework debugging]
ms.assetid: 3eb41151-a228-43e3-ba8f-e6dd3ceb8542
topic_type:
- apiref
ms.openlocfilehash: 401dfbea0da309db24f3052f462daa66e8bbef4a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449265"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="1b714-102">ISymUnmanagedConstant::GetSignature – metoda</span><span class="sxs-lookup"><span data-stu-id="1b714-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="1b714-103">Získá signaturu konstanty.</span><span class="sxs-lookup"><span data-stu-id="1b714-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b714-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b714-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b714-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1b714-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="1b714-106">pro Délka vyrovnávací paměti, na kterou parametr `pcSig` odkazuje.</span><span class="sxs-lookup"><span data-stu-id="1b714-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="1b714-107">mimo Ukazatel na `ULONG32`, který obdrží velikost vyrovnávací paměti, která je požadována k podpisu.</span><span class="sxs-lookup"><span data-stu-id="1b714-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="1b714-108">mimo Vyrovnávací paměť, která ukládá podpis.</span><span class="sxs-lookup"><span data-stu-id="1b714-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b714-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1b714-109">Return Value</span></span>  
 <span data-ttu-id="1b714-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="1b714-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b714-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1b714-111">Requirements</span></span>  
 <span data-ttu-id="1b714-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1b714-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b714-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1b714-113">See also</span></span>

- [<span data-ttu-id="1b714-114">ISymUnmanagedConstant – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b714-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="1b714-115">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="1b714-115">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="1b714-116">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="1b714-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
