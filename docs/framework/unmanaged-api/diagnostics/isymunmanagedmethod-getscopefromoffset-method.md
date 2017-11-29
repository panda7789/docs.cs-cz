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
ms.openlocfilehash: b863031cae487a2c081f23aeada1971893aa339f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="b840f-102">ISymUnmanagedMethod::GetScopeFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="b840f-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="b840f-103">Získá lexikální nejvíce vymezeném oboru v rámci této metody, která obklopuje daným posunem.</span><span class="sxs-lookup"><span data-stu-id="b840f-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="b840f-104">Tímto lze spustit místní proměnné hledání.</span><span class="sxs-lookup"><span data-stu-id="b840f-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b840f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b840f-105">Syntax</span></span>  
  
```  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b840f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b840f-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="b840f-107">[v] A `ULONG` obsahující posun.</span><span class="sxs-lookup"><span data-stu-id="b840f-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="b840f-108">[out] Ukazatele, který je nastavený s vráceným [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b840f-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b840f-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b840f-109">Return Value</span></span>  
 <span data-ttu-id="b840f-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="b840f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b840f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b840f-111">Requirements</span></span>  
 <span data-ttu-id="b840f-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b840f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b840f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="b840f-113">See Also</span></span>  
 [<span data-ttu-id="b840f-114">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b840f-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
