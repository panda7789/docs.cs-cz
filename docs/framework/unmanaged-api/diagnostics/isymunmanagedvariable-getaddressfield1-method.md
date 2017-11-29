---
title: "ISymUnmanagedVariable::GetAddressField1 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetAddressField1
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetAddressField1
helpviewer_keywords:
- GetAddressField1 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField1 method [.NET Framework debugging]
ms.assetid: 25788ed1-0ce3-4b97-96fc-88f8997812a3
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 460535813ed684424ae51710f09c731505805773
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="488d0-102">ISymUnmanagedVariable::GetAddressField1 – metoda</span><span class="sxs-lookup"><span data-stu-id="488d0-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>
<span data-ttu-id="488d0-103">Získá první pole adresy pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="488d0-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="488d0-104">Její význam závisí na druhu adresy.</span><span class="sxs-lookup"><span data-stu-id="488d0-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="488d0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="488d0-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="488d0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="488d0-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="488d0-107">[out] Ukazatel na `ULONG32` která přijme první pole adresy.</span><span class="sxs-lookup"><span data-stu-id="488d0-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="488d0-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="488d0-108">Return Value</span></span>  
 <span data-ttu-id="488d0-109">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="488d0-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="488d0-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="488d0-110">Requirements</span></span>  
 <span data-ttu-id="488d0-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="488d0-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="488d0-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="488d0-112">See Also</span></span>  
 [<span data-ttu-id="488d0-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="488d0-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="488d0-114">Getaddressfield2 – metoda</span><span class="sxs-lookup"><span data-stu-id="488d0-114">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)  
 [<span data-ttu-id="488d0-115">Getaddressfield3 – metoda</span><span class="sxs-lookup"><span data-stu-id="488d0-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)  
 [<span data-ttu-id="488d0-116">Getaddresskind – metoda</span><span class="sxs-lookup"><span data-stu-id="488d0-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
