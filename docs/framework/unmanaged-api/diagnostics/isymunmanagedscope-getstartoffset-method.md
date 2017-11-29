---
title: "ISymUnmanagedScope::GetStartOffset – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetStartOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetStartOffset method [.NET Framework debugging]
ms.assetid: da6bbc75-94d1-4354-9722-0d455b4428fb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8e24924607cad1922f2d1b5a816dc635eb6c7820
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="fddc4-102">ISymUnmanagedScope::GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="fddc4-102">ISymUnmanagedScope::GetStartOffset Method</span></span>
<span data-ttu-id="fddc4-103">Získá počáteční odsazení pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="fddc4-103">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fddc4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fddc4-104">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fddc4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fddc4-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="fddc4-106">[out] Ukazatel na `ULONG32` obsahující počáteční posun.</span><span class="sxs-lookup"><span data-stu-id="fddc4-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fddc4-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fddc4-107">Return Value</span></span>  
 <span data-ttu-id="fddc4-108">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="fddc4-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fddc4-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fddc4-109">Requirements</span></span>  
 <span data-ttu-id="fddc4-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fddc4-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fddc4-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="fddc4-111">See Also</span></span>  
 [<span data-ttu-id="fddc4-112">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fddc4-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="fddc4-113">Getendoffset – metoda</span><span class="sxs-lookup"><span data-stu-id="fddc4-113">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)
