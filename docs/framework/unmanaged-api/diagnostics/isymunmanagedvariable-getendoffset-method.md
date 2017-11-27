---
title: "ISymUnmanagedVariable::GetEndOffset – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetEndOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b7a2dac8425cd852c6c17ee1674710f6798d3b1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="bfb64-102">ISymUnmanagedVariable::GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="bfb64-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="bfb64-103">Získá posun end této proměnné v rámci jeho nadřazený objekt.</span><span class="sxs-lookup"><span data-stu-id="bfb64-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="bfb64-104">Pokud je to místní proměnné v oboru, posun end bude spadat do posuny definované pro obor.</span><span class="sxs-lookup"><span data-stu-id="bfb64-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfb64-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bfb64-105">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bfb64-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bfb64-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="bfb64-107">[out] Ukazatel na `ULONG32` která přijme posun end.</span><span class="sxs-lookup"><span data-stu-id="bfb64-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bfb64-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bfb64-108">Return Value</span></span>  
 <span data-ttu-id="bfb64-109">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="bfb64-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfb64-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bfb64-110">Requirements</span></span>  
 <span data-ttu-id="bfb64-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bfb64-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfb64-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="bfb64-112">See Also</span></span>  
 [<span data-ttu-id="bfb64-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bfb64-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="bfb64-114">Getstartoffset – metoda</span><span class="sxs-lookup"><span data-stu-id="bfb64-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
