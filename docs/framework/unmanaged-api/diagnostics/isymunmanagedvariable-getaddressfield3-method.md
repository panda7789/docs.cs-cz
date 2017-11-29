---
title: "ISymUnmanagedVariable::GetAddressField3 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetAddressField3
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetAddressField3
helpviewer_keywords:
- ISymUnmanagedVariable::GetAddressField3 method [.NET Framework debugging]
- GetAddressField3 method [.NET Framework debugging]
ms.assetid: 4d834721-ad8d-439d-b356-c6b4aef022fc
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1dfeb3f02b0c767dfc200a625fa4c617692dc11f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="b23f3-102">ISymUnmanagedVariable::GetAddressField3 – metoda</span><span class="sxs-lookup"><span data-stu-id="b23f3-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>
<span data-ttu-id="b23f3-103">Získá pole třetí adresa pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="b23f3-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="b23f3-104">Její význam závisí na druhu adresy.</span><span class="sxs-lookup"><span data-stu-id="b23f3-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b23f3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b23f3-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b23f3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b23f3-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="b23f3-107">[out] Ukazatel na `ULONG32` který přijímá pole třetí adresa.</span><span class="sxs-lookup"><span data-stu-id="b23f3-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b23f3-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b23f3-108">Return Value</span></span>  
 <span data-ttu-id="b23f3-109">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="b23f3-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b23f3-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b23f3-110">Requirements</span></span>  
 <span data-ttu-id="b23f3-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b23f3-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b23f3-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="b23f3-112">See Also</span></span>  
 [<span data-ttu-id="b23f3-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b23f3-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="b23f3-114">Getaddressfield1 – metoda</span><span class="sxs-lookup"><span data-stu-id="b23f3-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)  
 [<span data-ttu-id="b23f3-115">Getaddressfield2 – metoda</span><span class="sxs-lookup"><span data-stu-id="b23f3-115">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)  
 [<span data-ttu-id="b23f3-116">Getaddresskind – metoda</span><span class="sxs-lookup"><span data-stu-id="b23f3-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
