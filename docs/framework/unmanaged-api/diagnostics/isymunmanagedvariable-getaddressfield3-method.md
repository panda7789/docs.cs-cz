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
ms.openlocfilehash: ff888d3e2b86efeea3f4e3d33528f731d85886bf
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615264"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="d8f2b-102">ISymUnmanagedVariable::GetAddressField3 – metoda</span><span class="sxs-lookup"><span data-stu-id="d8f2b-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>
<span data-ttu-id="d8f2b-103">Získá třetí pole adresy pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="d8f2b-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="d8f2b-104">Jeho význam závisí na typu adresy.</span><span class="sxs-lookup"><span data-stu-id="d8f2b-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8f2b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8f2b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8f2b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8f2b-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="d8f2b-107">mimo Ukazatel na `ULONG32` , který obdrží třetí pole adresy.</span><span class="sxs-lookup"><span data-stu-id="d8f2b-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8f2b-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d8f2b-108">Return Value</span></span>  
 <span data-ttu-id="d8f2b-109">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="d8f2b-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8f2b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8f2b-110">Requirements</span></span>  
 <span data-ttu-id="d8f2b-111">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d8f2b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8f2b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8f2b-112">See also</span></span>

- [<span data-ttu-id="d8f2b-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8f2b-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="d8f2b-114">GetAddressField1 – metoda</span><span class="sxs-lookup"><span data-stu-id="d8f2b-114">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="d8f2b-115">GetAddressField2 – metoda</span><span class="sxs-lookup"><span data-stu-id="d8f2b-115">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="d8f2b-116">GetAddressKind – metoda</span><span class="sxs-lookup"><span data-stu-id="d8f2b-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
