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
ms.openlocfilehash: 3cad217ddf2d5354ad019f26fd10fb9ccd004d61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986193"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="25032-102">ISymUnmanagedScope::GetChildren – metoda</span><span class="sxs-lookup"><span data-stu-id="25032-102">ISymUnmanagedScope::GetChildren Method</span></span>
<span data-ttu-id="25032-103">Získá podřízené objekty tohoto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="25032-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25032-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25032-104">Syntax</span></span>  
  
```  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25032-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25032-105">Parameters</span></span>  
 `cChildren`  
 <span data-ttu-id="25032-106">[in] A `ULONG32` , který označuje velikost `children` pole.</span><span class="sxs-lookup"><span data-stu-id="25032-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="25032-107">[out] Ukazatel `ULONG32` , která obdrží velikost vyrovnávací paměti musí obsahovat podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="25032-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="25032-108">[out] Vrácené pole podřízené položky.</span><span class="sxs-lookup"><span data-stu-id="25032-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25032-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="25032-109">Return Value</span></span>  
 <span data-ttu-id="25032-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="25032-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25032-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25032-111">Requirements</span></span>  
 <span data-ttu-id="25032-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="25032-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25032-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25032-113">See also</span></span>

- [<span data-ttu-id="25032-114">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25032-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="25032-115">GetParent – metoda</span><span class="sxs-lookup"><span data-stu-id="25032-115">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)
