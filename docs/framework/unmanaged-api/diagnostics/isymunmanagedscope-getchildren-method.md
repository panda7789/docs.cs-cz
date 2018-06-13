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
ms.openlocfilehash: 3ce2372be02bc0bae7097389d4933f1f28a4ed79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427047"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="68d0a-102">ISymUnmanagedScope::GetChildren – metoda</span><span class="sxs-lookup"><span data-stu-id="68d0a-102">ISymUnmanagedScope::GetChildren Method</span></span>
<span data-ttu-id="68d0a-103">Získá podřízené objekty tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="68d0a-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68d0a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68d0a-104">Syntax</span></span>  
  
```  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68d0a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="68d0a-105">Parameters</span></span>  
 `cChildren`  
 <span data-ttu-id="68d0a-106">[v] A `ULONG32` určující velikost `children` pole.</span><span class="sxs-lookup"><span data-stu-id="68d0a-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="68d0a-107">[out] Ukazatel na `ULONG32` která přijme velikost vyrovnávací paměti musí obsahovat podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="68d0a-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="68d0a-108">[out] Pole vrácené podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="68d0a-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68d0a-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="68d0a-109">Return Value</span></span>  
 <span data-ttu-id="68d0a-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="68d0a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68d0a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="68d0a-111">Requirements</span></span>  
 <span data-ttu-id="68d0a-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="68d0a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68d0a-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="68d0a-113">See Also</span></span>  
 [<span data-ttu-id="68d0a-114">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68d0a-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="68d0a-115">GetParent – metoda</span><span class="sxs-lookup"><span data-stu-id="68d0a-115">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)
