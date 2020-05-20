---
title: ISymUnmanagedScope::GetNamespaces – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetNamespaces
helpviewer_keywords:
- GetNamespaces method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetNamespaces method [.NET Framework debugging]
ms.assetid: c44b0440-04bd-460a-84fb-41afecf44503
topic_type:
- apiref
ms.openlocfilehash: 6f11a69671864ba4627c2bb8c86e0c9beb27eeb1
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83611117"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="cc6ae-102">ISymUnmanagedScope::GetNamespaces – metoda</span><span class="sxs-lookup"><span data-stu-id="cc6ae-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="cc6ae-103">Načte obory názvů, které jsou používány v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="cc6ae-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc6ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc6ae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc6ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc6ae-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="cc6ae-106">pro Velikost `namespaces` pole.</span><span class="sxs-lookup"><span data-stu-id="cc6ae-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="cc6ae-107">mimo Ukazatel na `ULONG32` , který přijímá velikost vyrovnávací paměti vyžadované k omezení oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cc6ae-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="cc6ae-108">mimo Pole, které přijímá obory názvů.</span><span class="sxs-lookup"><span data-stu-id="cc6ae-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc6ae-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cc6ae-109">Return Value</span></span>  
 <span data-ttu-id="cc6ae-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="cc6ae-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc6ae-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc6ae-111">Requirements</span></span>  
 <span data-ttu-id="cc6ae-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="cc6ae-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc6ae-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc6ae-113">See also</span></span>

- [<span data-ttu-id="cc6ae-114">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc6ae-114">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
