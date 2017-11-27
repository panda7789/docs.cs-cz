---
title: "ISymUnmanagedVariable::GetAddressField2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetAddressField2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetAddressField2
helpviewer_keywords:
- GetAddressField2 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField2 method [.NET Framework debugging]
ms.assetid: 1f25b294-72b6-4882-a49b-6c9d364b6008
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d3e9124cb800416c44596d7b6f21a21c416e0e94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="39caa-102">ISymUnmanagedVariable::GetAddressField2 – metoda</span><span class="sxs-lookup"><span data-stu-id="39caa-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>
<span data-ttu-id="39caa-103">Získá druhý pole adresy pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="39caa-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="39caa-104">Její význam závisí na druhu adresy.</span><span class="sxs-lookup"><span data-stu-id="39caa-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39caa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39caa-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="39caa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="39caa-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="39caa-107">[out] Ukazatel na `ULONG32` která přijme druhé pole adresy.</span><span class="sxs-lookup"><span data-stu-id="39caa-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39caa-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="39caa-108">Return Value</span></span>  
 <span data-ttu-id="39caa-109">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="39caa-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39caa-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="39caa-110">Requirements</span></span>  
 <span data-ttu-id="39caa-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="39caa-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39caa-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="39caa-112">See Also</span></span>  
 [<span data-ttu-id="39caa-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="39caa-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="39caa-114">Getaddressfield1 – metoda</span><span class="sxs-lookup"><span data-stu-id="39caa-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)  
 [<span data-ttu-id="39caa-115">Getaddressfield3 – metoda</span><span class="sxs-lookup"><span data-stu-id="39caa-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)  
 [<span data-ttu-id="39caa-116">Getaddresskind – metoda</span><span class="sxs-lookup"><span data-stu-id="39caa-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
