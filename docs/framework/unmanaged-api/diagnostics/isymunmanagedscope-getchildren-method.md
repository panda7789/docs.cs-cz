---
title: ISymUnmanagedScope::GetChildren – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetChildren
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ffc4d5a1e6b8f1acc7603e9c2e01216e3188989e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751303"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="2f6b5-102">ISymUnmanagedScope::GetChildren – metoda</span><span class="sxs-lookup"><span data-stu-id="2f6b5-102">ISymUnmanagedScope::GetChildren Method</span></span>
<span data-ttu-id="2f6b5-103">Získá podřízené objekty tohoto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="2f6b5-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f6b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f6b5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f6b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f6b5-105">Parameters</span></span>  
 `cChildren`  
 <span data-ttu-id="2f6b5-106">[in] A `ULONG32` , který označuje velikost `children` pole.</span><span class="sxs-lookup"><span data-stu-id="2f6b5-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="2f6b5-107">[out] Ukazatel `ULONG32` , která obdrží velikost vyrovnávací paměti musí obsahovat podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="2f6b5-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="2f6b5-108">[out] Vrácené pole podřízené položky.</span><span class="sxs-lookup"><span data-stu-id="2f6b5-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f6b5-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2f6b5-109">Return Value</span></span>  
 <span data-ttu-id="2f6b5-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="2f6b5-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f6b5-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f6b5-111">Requirements</span></span>  
 <span data-ttu-id="2f6b5-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2f6b5-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f6b5-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f6b5-113">See also</span></span>

- [<span data-ttu-id="2f6b5-114">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f6b5-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="2f6b5-115">GetParent – metoda</span><span class="sxs-lookup"><span data-stu-id="2f6b5-115">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)
