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
ms.openlocfilehash: 781111db30ae664c9dd45744f88387e161f2716f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426796"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="eee5f-102">ISymUnmanagedScope::GetLocals – metoda</span><span class="sxs-lookup"><span data-stu-id="eee5f-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="eee5f-103">Získá místní proměnné definované v tomto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="eee5f-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eee5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eee5f-104">Syntax</span></span>  
  
```  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eee5f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eee5f-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="eee5f-106">[v] A `ULONG32` určující velikost `locals` pole.</span><span class="sxs-lookup"><span data-stu-id="eee5f-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="eee5f-107">[out] Ukazatel na `ULONG32` která přijme velikost vyrovnávací paměti musí obsahovat místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="eee5f-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="eee5f-108">[out] Pole, která přijímá místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="eee5f-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eee5f-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="eee5f-109">Return Value</span></span>  
 <span data-ttu-id="eee5f-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="eee5f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eee5f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eee5f-111">Requirements</span></span>  
 <span data-ttu-id="eee5f-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="eee5f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eee5f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="eee5f-113">See Also</span></span>  
 [<span data-ttu-id="eee5f-114">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eee5f-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
