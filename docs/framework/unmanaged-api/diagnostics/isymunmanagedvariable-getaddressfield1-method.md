---
title: "ISymUnmanagedVariable::GetAddressField1 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8085deb0cdb0b16eddfa39663277ceecdde10341
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="368e2-102">ISymUnmanagedVariable::GetAddressField1 – metoda</span><span class="sxs-lookup"><span data-stu-id="368e2-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>
<span data-ttu-id="368e2-103">Získá první pole adresy pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="368e2-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="368e2-104">Její význam závisí na druhu adresy.</span><span class="sxs-lookup"><span data-stu-id="368e2-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="368e2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="368e2-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="368e2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="368e2-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="368e2-107">[out] Ukazatel na `ULONG32` která přijme první pole adresy.</span><span class="sxs-lookup"><span data-stu-id="368e2-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="368e2-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="368e2-108">Return Value</span></span>  
 <span data-ttu-id="368e2-109">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="368e2-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="368e2-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="368e2-110">Requirements</span></span>  
 <span data-ttu-id="368e2-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="368e2-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="368e2-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="368e2-112">See Also</span></span>  
 [<span data-ttu-id="368e2-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="368e2-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="368e2-114">GetAddressField2 – metoda</span><span class="sxs-lookup"><span data-stu-id="368e2-114">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)  
 [<span data-ttu-id="368e2-115">GetAddressField3 – metoda</span><span class="sxs-lookup"><span data-stu-id="368e2-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)  
 [<span data-ttu-id="368e2-116">GetAddressKind – metoda</span><span class="sxs-lookup"><span data-stu-id="368e2-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
