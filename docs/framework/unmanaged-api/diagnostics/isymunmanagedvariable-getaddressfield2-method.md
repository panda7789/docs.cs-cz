---
title: ISymUnmanagedVariable::GetAddressField2 – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField2
helpviewer_keywords:
- GetAddressField2 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField2 method [.NET Framework debugging]
ms.assetid: 1f25b294-72b6-4882-a49b-6c9d364b6008
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2030a0da7a84695750d1dd9781adca9cd66f22ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797615"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="cedd6-102">ISymUnmanagedVariable::GetAddressField2 – metoda</span><span class="sxs-lookup"><span data-stu-id="cedd6-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>
<span data-ttu-id="cedd6-103">Získá druhý pole adresy pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="cedd6-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="cedd6-104">Její význam závisí na druhu adresu.</span><span class="sxs-lookup"><span data-stu-id="cedd6-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cedd6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cedd6-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cedd6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cedd6-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="cedd6-107">[out] Ukazatel `ULONG32` , která obdrží druhé pole adresu.</span><span class="sxs-lookup"><span data-stu-id="cedd6-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cedd6-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cedd6-108">Return Value</span></span>  
 <span data-ttu-id="cedd6-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="cedd6-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cedd6-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cedd6-110">Requirements</span></span>  
 <span data-ttu-id="cedd6-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cedd6-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cedd6-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cedd6-112">See also</span></span>

- [<span data-ttu-id="cedd6-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cedd6-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="cedd6-114">GetAddressField1 – metoda</span><span class="sxs-lookup"><span data-stu-id="cedd6-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="cedd6-115">GetAddressField3 – metoda</span><span class="sxs-lookup"><span data-stu-id="cedd6-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="cedd6-116">GetAddressKind – metoda</span><span class="sxs-lookup"><span data-stu-id="cedd6-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
