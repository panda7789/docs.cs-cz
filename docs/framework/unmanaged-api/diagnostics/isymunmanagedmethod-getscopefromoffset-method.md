---
title: "ISymUnmanagedMethod::GetScopeFromOffset – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetScopeFromOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 890fd702bc2edb5714dc9c91a618c6420a11a27a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="6e1b7-102">ISymUnmanagedMethod::GetScopeFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="6e1b7-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="6e1b7-103">Získá lexikální nejvíce vymezeném oboru v rámci této metody, která obklopuje daným posunem.</span><span class="sxs-lookup"><span data-stu-id="6e1b7-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="6e1b7-104">Tímto lze spustit místní proměnné hledání.</span><span class="sxs-lookup"><span data-stu-id="6e1b7-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e1b7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e1b7-105">Syntax</span></span>  
  
```  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e1b7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e1b7-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="6e1b7-107">[v] A `ULONG` obsahující posun.</span><span class="sxs-lookup"><span data-stu-id="6e1b7-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="6e1b7-108">[out] Ukazatele, který je nastavený s vráceným [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6e1b7-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e1b7-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6e1b7-109">Return Value</span></span>  
 <span data-ttu-id="6e1b7-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="6e1b7-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e1b7-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e1b7-111">Requirements</span></span>  
 <span data-ttu-id="6e1b7-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6e1b7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e1b7-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e1b7-113">See Also</span></span>  
 [<span data-ttu-id="6e1b7-114">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e1b7-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
