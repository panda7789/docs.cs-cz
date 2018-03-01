---
title: "ISymUnmanagedVariable::GetStartOffset – metoda"
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
- ISymUnmanagedVariable.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b3fa0c710eb5de8b9a92970002336de22adb2458
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="486a5-102">ISymUnmanagedVariable::GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="486a5-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="486a5-103">Získá počáteční odsazení této proměnné v rámci jeho nadřazený objekt.</span><span class="sxs-lookup"><span data-stu-id="486a5-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="486a5-104">Pokud je to místní proměnné v oboru, počáteční odsazení bude spadat do posuny definované pro obor.</span><span class="sxs-lookup"><span data-stu-id="486a5-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="486a5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="486a5-105">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="486a5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="486a5-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="486a5-107">[out] Ukazatel na `ULONG32` která přijme počáteční odsazení.</span><span class="sxs-lookup"><span data-stu-id="486a5-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="486a5-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="486a5-108">Return Value</span></span>  
 <span data-ttu-id="486a5-109">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="486a5-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="486a5-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="486a5-110">Requirements</span></span>  
 <span data-ttu-id="486a5-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="486a5-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="486a5-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="486a5-112">See Also</span></span>  
 [<span data-ttu-id="486a5-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="486a5-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="486a5-114">GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="486a5-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)
