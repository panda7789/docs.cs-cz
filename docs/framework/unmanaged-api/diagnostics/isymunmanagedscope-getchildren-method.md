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
ms.openlocfilehash: c7e9d2fe94c33127d8b105333ad6dac9d6cc5af6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446369"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="e0ecc-102">ISymUnmanagedScope::GetChildren – metoda</span><span class="sxs-lookup"><span data-stu-id="e0ecc-102">ISymUnmanagedScope::GetChildren Method</span></span>
<span data-ttu-id="e0ecc-103">Získá podřízené objekty tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="e0ecc-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0ecc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0ecc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0ecc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0ecc-105">Parameters</span></span>  
 `cChildren`  
 <span data-ttu-id="e0ecc-106">pro `ULONG32`, která určuje velikost `children` pole.</span><span class="sxs-lookup"><span data-stu-id="e0ecc-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="e0ecc-107">mimo Ukazatel na `ULONG32`, který přijímá velikost vyrovnávací paměti vyžadované k uložení podřízených objektů.</span><span class="sxs-lookup"><span data-stu-id="e0ecc-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="e0ecc-108">mimo Vrácené pole podřízených objektů.</span><span class="sxs-lookup"><span data-stu-id="e0ecc-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0ecc-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e0ecc-109">Return Value</span></span>  
 <span data-ttu-id="e0ecc-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="e0ecc-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0ecc-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0ecc-111">Requirements</span></span>  
 <span data-ttu-id="e0ecc-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e0ecc-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0ecc-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0ecc-113">See also</span></span>

- [<span data-ttu-id="e0ecc-114">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e0ecc-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="e0ecc-115">GetParent – metoda</span><span class="sxs-lookup"><span data-stu-id="e0ecc-115">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)
