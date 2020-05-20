---
title: ISymUnmanagedReader::GetNamespaces – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedReader::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 3feb4796-2fab-45ce-beca-6f5bc530b971
topic_type:
- apiref
ms.openlocfilehash: 44f9284f0a89f0941940cf379c48b2b138149122
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614939"
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="a7c51-102">ISymUnmanagedReader::GetNamespaces – metoda</span><span class="sxs-lookup"><span data-stu-id="a7c51-102">ISymUnmanagedReader::GetNamespaces Method</span></span>
<span data-ttu-id="a7c51-103">Načte obory názvů definované v globálním oboru v rámci tohoto úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="a7c51-103">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7c51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7c51-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7c51-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7c51-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="a7c51-106">pro Velikost pole obory názvů.</span><span class="sxs-lookup"><span data-stu-id="a7c51-106">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="a7c51-107">mimo Ukazatel na proměnnou, která přijímá délku seznamu oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="a7c51-107">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="a7c51-108">mimo Ukazatel na proměnnou, která přijímá seznam oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="a7c51-108">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7c51-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a7c51-109">Return Value</span></span>  
 <span data-ttu-id="a7c51-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="a7c51-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7c51-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a7c51-111">Requirements</span></span>  
 <span data-ttu-id="a7c51-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a7c51-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7c51-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7c51-113">See also</span></span>

- [<span data-ttu-id="a7c51-114">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a7c51-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
