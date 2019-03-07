---
title: ISymUnmanagedScope::GetLocals – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocals
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocals
helpviewer_keywords:
- GetLocals method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocals method [.NET Framework debugging]
ms.assetid: 17c45f15-8c44-44da-b070-f902077b36e4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d6c48a7ae62155dc558fb4a62b3e2573bea77594
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499170"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="37465-102">ISymUnmanagedScope::GetLocals – metoda</span><span class="sxs-lookup"><span data-stu-id="37465-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="37465-103">Získá místní proměnné definované v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="37465-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37465-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37465-104">Syntax</span></span>  
  
```  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37465-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37465-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="37465-106">[in] A `ULONG32` , který označuje velikost `locals` pole.</span><span class="sxs-lookup"><span data-stu-id="37465-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="37465-107">[out] Ukazatel `ULONG32` , která obdrží velikost vyrovnávací paměti musí obsahovat místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="37465-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="37465-108">[out] Pole, která přijímá místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="37465-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37465-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="37465-109">Return Value</span></span>  
 <span data-ttu-id="37465-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="37465-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37465-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37465-111">Requirements</span></span>  
 <span data-ttu-id="37465-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="37465-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37465-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37465-113">See also</span></span>
- [<span data-ttu-id="37465-114">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37465-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
