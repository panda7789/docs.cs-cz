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
ms.openlocfilehash: 0898d554a2602a1139f2e37eb67f3aa00c5bd79e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436082"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="acdb0-102">ISymUnmanagedMethod::GetScopeFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="acdb0-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="acdb0-103">Získá lexikální nejvíce vymezeném oboru v rámci této metody, která obklopuje daným posunem.</span><span class="sxs-lookup"><span data-stu-id="acdb0-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="acdb0-104">Tímto lze spustit místní proměnné hledání.</span><span class="sxs-lookup"><span data-stu-id="acdb0-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acdb0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acdb0-105">Syntax</span></span>  
  
```  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="acdb0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="acdb0-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="acdb0-107">[v] A `ULONG` obsahující posun.</span><span class="sxs-lookup"><span data-stu-id="acdb0-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="acdb0-108">[out] Ukazatele, který je nastavený s vráceným [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="acdb0-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="acdb0-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="acdb0-109">Return Value</span></span>  
 <span data-ttu-id="acdb0-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="acdb0-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acdb0-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="acdb0-111">Requirements</span></span>  
 <span data-ttu-id="acdb0-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="acdb0-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acdb0-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="acdb0-113">See Also</span></span>  
 [<span data-ttu-id="acdb0-114">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="acdb0-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
