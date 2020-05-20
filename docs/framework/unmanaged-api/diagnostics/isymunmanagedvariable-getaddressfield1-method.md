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
ms.openlocfilehash: 253fd17178c03bc0c4d8ea031888a404ad56f876
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615277"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="d0d37-102">ISymUnmanagedVariable::GetAddressField1 – metoda</span><span class="sxs-lookup"><span data-stu-id="d0d37-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>
<span data-ttu-id="d0d37-103">Získá první pole adresy pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="d0d37-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="d0d37-104">Jeho význam závisí na typu adresy.</span><span class="sxs-lookup"><span data-stu-id="d0d37-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0d37-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0d37-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0d37-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0d37-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="d0d37-107">mimo Ukazatel na `ULONG32` , který obdrží první pole adresy.</span><span class="sxs-lookup"><span data-stu-id="d0d37-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0d37-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d0d37-108">Return Value</span></span>  
 <span data-ttu-id="d0d37-109">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="d0d37-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0d37-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0d37-110">Requirements</span></span>  
 <span data-ttu-id="d0d37-111">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d0d37-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0d37-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0d37-112">See also</span></span>

- [<span data-ttu-id="d0d37-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0d37-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="d0d37-114">GetAddressField2 – metoda</span><span class="sxs-lookup"><span data-stu-id="d0d37-114">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="d0d37-115">GetAddressField3 – metoda</span><span class="sxs-lookup"><span data-stu-id="d0d37-115">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="d0d37-116">GetAddressKind – metoda</span><span class="sxs-lookup"><span data-stu-id="d0d37-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
