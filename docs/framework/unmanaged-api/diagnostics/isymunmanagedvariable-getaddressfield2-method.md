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
ms.openlocfilehash: 6256d052780b1c610e61267be2517954d722a42d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610597"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="4119f-102">ISymUnmanagedVariable::GetAddressField2 – metoda</span><span class="sxs-lookup"><span data-stu-id="4119f-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>
<span data-ttu-id="4119f-103">Získá druhé pole adresy pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="4119f-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="4119f-104">Jeho význam závisí na typu adresy.</span><span class="sxs-lookup"><span data-stu-id="4119f-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4119f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4119f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4119f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4119f-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="4119f-107">mimo Ukazatel na `ULONG32` , který obdrží druhé pole adresy.</span><span class="sxs-lookup"><span data-stu-id="4119f-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4119f-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4119f-108">Return Value</span></span>  
 <span data-ttu-id="4119f-109">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="4119f-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4119f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4119f-110">Requirements</span></span>  
 <span data-ttu-id="4119f-111">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4119f-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4119f-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="4119f-112">See also</span></span>

- [<span data-ttu-id="4119f-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4119f-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="4119f-114">GetAddressField1 – metoda</span><span class="sxs-lookup"><span data-stu-id="4119f-114">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="4119f-115">GetAddressField3 – metoda</span><span class="sxs-lookup"><span data-stu-id="4119f-115">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="4119f-116">GetAddressKind – metoda</span><span class="sxs-lookup"><span data-stu-id="4119f-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
