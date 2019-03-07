---
title: ISymUnmanagedVariable::GetAddressField3 – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField3
helpviewer_keywords:
- ISymUnmanagedVariable::GetAddressField3 method [.NET Framework debugging]
- GetAddressField3 method [.NET Framework debugging]
ms.assetid: 4d834721-ad8d-439d-b356-c6b4aef022fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0838ac08ff69e33a0badef7c0f52cb6189be2b7f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469037"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="5263b-102">ISymUnmanagedVariable::GetAddressField3 – metoda</span><span class="sxs-lookup"><span data-stu-id="5263b-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>
<span data-ttu-id="5263b-103">Získá pole třetí adresa pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="5263b-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="5263b-104">Její význam závisí na druhu adresu.</span><span class="sxs-lookup"><span data-stu-id="5263b-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5263b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5263b-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5263b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5263b-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="5263b-107">[out] Ukazatel `ULONG32` , který přijímá pole třetí adresa.</span><span class="sxs-lookup"><span data-stu-id="5263b-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5263b-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5263b-108">Return Value</span></span>  
 <span data-ttu-id="5263b-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="5263b-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5263b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5263b-110">Requirements</span></span>  
 <span data-ttu-id="5263b-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5263b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5263b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5263b-112">See also</span></span>
- [<span data-ttu-id="5263b-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5263b-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="5263b-114">GetAddressField1 – metoda</span><span class="sxs-lookup"><span data-stu-id="5263b-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="5263b-115">GetAddressField2 – metoda</span><span class="sxs-lookup"><span data-stu-id="5263b-115">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="5263b-116">GetAddressKind – metoda</span><span class="sxs-lookup"><span data-stu-id="5263b-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
