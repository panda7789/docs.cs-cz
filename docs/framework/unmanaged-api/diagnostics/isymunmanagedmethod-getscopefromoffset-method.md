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
ms.openlocfilehash: d540318dabd55e9a520aedde371e0a83d612721e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759487"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="48ac1-102">ISymUnmanagedMethod::GetScopeFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="48ac1-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="48ac1-103">Získá nejvíce nadřazeného oboru lexikální v rámci této metody, které obklopuje dané posun.</span><span class="sxs-lookup"><span data-stu-id="48ac1-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="48ac1-104">To je možné spustit místní proměnné vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="48ac1-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48ac1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48ac1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48ac1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="48ac1-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="48ac1-107">[in] A `ULONG` obsahující posun.</span><span class="sxs-lookup"><span data-stu-id="48ac1-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="48ac1-108">[out] Ukazatel, který je nastaven na vrácenou [isymunmanagedscope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="48ac1-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48ac1-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="48ac1-109">Return Value</span></span>  
 <span data-ttu-id="48ac1-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="48ac1-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48ac1-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="48ac1-111">Requirements</span></span>  
 <span data-ttu-id="48ac1-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="48ac1-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48ac1-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48ac1-113">See also</span></span>

- [<span data-ttu-id="48ac1-114">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="48ac1-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
