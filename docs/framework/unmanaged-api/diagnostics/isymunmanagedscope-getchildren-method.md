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
ms.openlocfilehash: c6d21f40c260890c9c88dcdfccd7e31161024ba3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614861"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="c9bd7-102">ISymUnmanagedScope::GetChildren – metoda</span><span class="sxs-lookup"><span data-stu-id="c9bd7-102">ISymUnmanagedScope::GetChildren Method</span></span>
<span data-ttu-id="c9bd7-103">Získá podřízené objekty tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="c9bd7-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9bd7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9bd7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9bd7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9bd7-105">Parameters</span></span>  
 `cChildren`  
 <span data-ttu-id="c9bd7-106">pro `ULONG32`Který označuje velikost `children` pole.</span><span class="sxs-lookup"><span data-stu-id="c9bd7-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="c9bd7-107">mimo Ukazatel na `ULONG32` , který přijímá velikost vyrovnávací paměti vyžadované k uložení podřízených objektů.</span><span class="sxs-lookup"><span data-stu-id="c9bd7-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="c9bd7-108">mimo Vrácené pole podřízených objektů.</span><span class="sxs-lookup"><span data-stu-id="c9bd7-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9bd7-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c9bd7-109">Return Value</span></span>  
 <span data-ttu-id="c9bd7-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="c9bd7-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9bd7-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9bd7-111">Requirements</span></span>  
 <span data-ttu-id="c9bd7-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c9bd7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9bd7-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9bd7-113">See also</span></span>

- [<span data-ttu-id="c9bd7-114">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9bd7-114">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="c9bd7-115">GetParent – metoda</span><span class="sxs-lookup"><span data-stu-id="c9bd7-115">GetParent Method</span></span>](isymunmanagedscope-getparent-method.md)
