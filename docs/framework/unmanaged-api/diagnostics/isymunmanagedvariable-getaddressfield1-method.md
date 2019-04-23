---
title: ISymUnmanagedVariable::GetAddressField1 – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField1
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField1
helpviewer_keywords:
- GetAddressField1 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField1 method [.NET Framework debugging]
ms.assetid: 25788ed1-0ce3-4b97-96fc-88f8997812a3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67634024b04e82aa3a3c0b96dc260114c4c16371
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179696"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="78f59-102">ISymUnmanagedVariable::GetAddressField1 – metoda</span><span class="sxs-lookup"><span data-stu-id="78f59-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>
<span data-ttu-id="78f59-103">Získá první pole adresy pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="78f59-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="78f59-104">Její význam závisí na druhu adresu.</span><span class="sxs-lookup"><span data-stu-id="78f59-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78f59-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78f59-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78f59-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="78f59-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="78f59-107">[out] Ukazatel `ULONG32` , který přijímá pole první adresa.</span><span class="sxs-lookup"><span data-stu-id="78f59-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78f59-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="78f59-108">Return Value</span></span>  
 <span data-ttu-id="78f59-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="78f59-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78f59-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78f59-110">Requirements</span></span>  
 <span data-ttu-id="78f59-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="78f59-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78f59-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78f59-112">See also</span></span>

- [<span data-ttu-id="78f59-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78f59-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="78f59-114">GetAddressField2 – metoda</span><span class="sxs-lookup"><span data-stu-id="78f59-114">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="78f59-115">GetAddressField3 – metoda</span><span class="sxs-lookup"><span data-stu-id="78f59-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="78f59-116">GetAddressKind – metoda</span><span class="sxs-lookup"><span data-stu-id="78f59-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
