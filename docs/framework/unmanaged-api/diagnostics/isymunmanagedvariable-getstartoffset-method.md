---
title: "ISymUnmanagedVariable::GetStartOffset – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetStartOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5b7fd3a64202224ef5a7cc348ee8e9974a664d09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="81754-102">ISymUnmanagedVariable::GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="81754-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="81754-103">Získá počáteční odsazení této proměnné v rámci jeho nadřazený objekt.</span><span class="sxs-lookup"><span data-stu-id="81754-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="81754-104">Pokud je to místní proměnné v oboru, počáteční odsazení bude spadat do posuny definované pro obor.</span><span class="sxs-lookup"><span data-stu-id="81754-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81754-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81754-105">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81754-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="81754-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="81754-107">[out] Ukazatel na `ULONG32` která přijme počáteční odsazení.</span><span class="sxs-lookup"><span data-stu-id="81754-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81754-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="81754-108">Return Value</span></span>  
 <span data-ttu-id="81754-109">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="81754-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81754-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="81754-110">Requirements</span></span>  
 <span data-ttu-id="81754-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="81754-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81754-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="81754-112">See Also</span></span>  
 [<span data-ttu-id="81754-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="81754-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="81754-114">Getendoffset – metoda</span><span class="sxs-lookup"><span data-stu-id="81754-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)
