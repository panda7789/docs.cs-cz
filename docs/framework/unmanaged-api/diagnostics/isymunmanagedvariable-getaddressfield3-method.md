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
ms.workload: dotnet
ms.openlocfilehash: eb7bfa17729321df21dfc69c79d65baf2a92a44a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="e906e-102">ISymUnmanagedVariable::GetAddressField3 – metoda</span><span class="sxs-lookup"><span data-stu-id="e906e-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>
<span data-ttu-id="e906e-103">Získá pole třetí adresa pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="e906e-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="e906e-104">Její význam závisí na druhu adresy.</span><span class="sxs-lookup"><span data-stu-id="e906e-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e906e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e906e-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e906e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e906e-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="e906e-107">[out] Ukazatel na `ULONG32` který přijímá pole třetí adresa.</span><span class="sxs-lookup"><span data-stu-id="e906e-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e906e-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e906e-108">Return Value</span></span>  
 <span data-ttu-id="e906e-109">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="e906e-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e906e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e906e-110">Requirements</span></span>  
 <span data-ttu-id="e906e-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e906e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e906e-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="e906e-112">See Also</span></span>  
 [<span data-ttu-id="e906e-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e906e-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="e906e-114">GetAddressField1 – metoda</span><span class="sxs-lookup"><span data-stu-id="e906e-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)  
 [<span data-ttu-id="e906e-115">GetAddressField2 – metoda</span><span class="sxs-lookup"><span data-stu-id="e906e-115">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)  
 [<span data-ttu-id="e906e-116">GetAddressKind – metoda</span><span class="sxs-lookup"><span data-stu-id="e906e-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
