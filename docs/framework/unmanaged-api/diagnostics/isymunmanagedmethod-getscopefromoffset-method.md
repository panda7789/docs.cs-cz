---
title: ISymUnmanagedMethod::GetScopeFromOffset – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetScopeFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5422e781ab2f494e85f637219aa540bf4ac34cb8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629732"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="ccd42-102">ISymUnmanagedMethod::GetScopeFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="ccd42-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="ccd42-103">Získá nejvíce nadřazeného oboru lexikální v rámci této metody, které obklopuje dané posun.</span><span class="sxs-lookup"><span data-stu-id="ccd42-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="ccd42-104">To je možné spustit místní proměnné vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="ccd42-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccd42-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccd42-105">Syntax</span></span>  
  
```  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ccd42-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ccd42-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="ccd42-107">[in] A `ULONG` obsahující posun.</span><span class="sxs-lookup"><span data-stu-id="ccd42-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ccd42-108">[out] Ukazatel, který je nastaven na vrácenou [isymunmanagedscope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ccd42-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ccd42-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ccd42-109">Return Value</span></span>  
 <span data-ttu-id="ccd42-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="ccd42-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccd42-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ccd42-111">Requirements</span></span>  
 <span data-ttu-id="ccd42-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ccd42-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccd42-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ccd42-113">See also</span></span>
- [<span data-ttu-id="ccd42-114">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ccd42-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
