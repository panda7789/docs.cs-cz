---
title: "ISymUnmanagedScope::GetLocals – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetLocals
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetLocals
helpviewer_keywords:
- GetLocals method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocals method [.NET Framework debugging]
ms.assetid: 17c45f15-8c44-44da-b070-f902077b36e4
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 76a52d0bd754dde8ded193dee38eaea895223b9d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="235ce-102">ISymUnmanagedScope::GetLocals – metoda</span><span class="sxs-lookup"><span data-stu-id="235ce-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="235ce-103">Získá místní proměnné definované v tomto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="235ce-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="235ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="235ce-104">Syntax</span></span>  
  
```  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="235ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="235ce-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="235ce-106">[v] A `ULONG32` určující velikost `locals` pole.</span><span class="sxs-lookup"><span data-stu-id="235ce-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="235ce-107">[out] Ukazatel na `ULONG32` která přijme velikost vyrovnávací paměti musí obsahovat místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="235ce-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="235ce-108">[out] Pole, která přijímá místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="235ce-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="235ce-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="235ce-109">Return Value</span></span>  
 <span data-ttu-id="235ce-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="235ce-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="235ce-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="235ce-111">Requirements</span></span>  
 <span data-ttu-id="235ce-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="235ce-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="235ce-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="235ce-113">See Also</span></span>  
 [<span data-ttu-id="235ce-114">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="235ce-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
