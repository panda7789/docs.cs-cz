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
ms.openlocfilehash: 463416165d2dbd7724d5cf0d29e40d8243ade34b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778316"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="79ecb-102">ISymUnmanagedVariable::GetAddressField2 – metoda</span><span class="sxs-lookup"><span data-stu-id="79ecb-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>
<span data-ttu-id="79ecb-103">Získá druhý pole adresy pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="79ecb-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="79ecb-104">Její význam závisí na druhu adresu.</span><span class="sxs-lookup"><span data-stu-id="79ecb-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79ecb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79ecb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79ecb-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="79ecb-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="79ecb-107">[out] Ukazatel `ULONG32` , která obdrží druhé pole adresu.</span><span class="sxs-lookup"><span data-stu-id="79ecb-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79ecb-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="79ecb-108">Return Value</span></span>  
 <span data-ttu-id="79ecb-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="79ecb-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79ecb-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="79ecb-110">Requirements</span></span>  
 <span data-ttu-id="79ecb-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="79ecb-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79ecb-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79ecb-112">See also</span></span>

- [<span data-ttu-id="79ecb-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="79ecb-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="79ecb-114">GetAddressField1 – metoda</span><span class="sxs-lookup"><span data-stu-id="79ecb-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="79ecb-115">GetAddressField3 – metoda</span><span class="sxs-lookup"><span data-stu-id="79ecb-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="79ecb-116">GetAddressKind – metoda</span><span class="sxs-lookup"><span data-stu-id="79ecb-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
