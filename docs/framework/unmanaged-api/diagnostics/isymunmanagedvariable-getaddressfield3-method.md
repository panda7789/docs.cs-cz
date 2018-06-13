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
ms.openlocfilehash: dd474c7f149b8eff542b674c2ba6527b6a0cbcb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426995"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="06aa1-102">ISymUnmanagedVariable::GetAddressField3 – metoda</span><span class="sxs-lookup"><span data-stu-id="06aa1-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>
<span data-ttu-id="06aa1-103">Získá pole třetí adresa pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="06aa1-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="06aa1-104">Její význam závisí na druhu adresy.</span><span class="sxs-lookup"><span data-stu-id="06aa1-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06aa1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06aa1-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="06aa1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="06aa1-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="06aa1-107">[out] Ukazatel na `ULONG32` který přijímá pole třetí adresa.</span><span class="sxs-lookup"><span data-stu-id="06aa1-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06aa1-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="06aa1-108">Return Value</span></span>  
 <span data-ttu-id="06aa1-109">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="06aa1-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06aa1-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06aa1-110">Requirements</span></span>  
 <span data-ttu-id="06aa1-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="06aa1-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06aa1-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="06aa1-112">See Also</span></span>  
 [<span data-ttu-id="06aa1-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06aa1-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="06aa1-114">GetAddressField1 – metoda</span><span class="sxs-lookup"><span data-stu-id="06aa1-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)  
 [<span data-ttu-id="06aa1-115">GetAddressField2 – metoda</span><span class="sxs-lookup"><span data-stu-id="06aa1-115">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)  
 [<span data-ttu-id="06aa1-116">GetAddressKind – metoda</span><span class="sxs-lookup"><span data-stu-id="06aa1-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
