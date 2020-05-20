---
title: ISymUnmanagedNamespace::GetNamespaces – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedNamespace::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 0ea9d9af-8709-4a46-872b-f54d9e840088
topic_type:
- apiref
ms.openlocfilehash: 48c50ac6be6d525676d85578e5a55a27104c180a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615095"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="74936-102">ISymUnmanagedNamespace::GetNamespaces – metoda</span><span class="sxs-lookup"><span data-stu-id="74936-102">ISymUnmanagedNamespace::GetNamespaces Method</span></span>
<span data-ttu-id="74936-103">Získá podřízené objekty tohoto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="74936-103">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74936-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74936-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74936-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="74936-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="74936-106">pro `ULONG32`Který označuje velikost `namespaces` pole.</span><span class="sxs-lookup"><span data-stu-id="74936-106">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="74936-107">mimo Ukazatel na `ULONG32` , který přijímá velikost vyrovnávací paměti, která je nutná k omezení oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="74936-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="74936-108">mimo Ukazatel na vyrovnávací paměť, která obsahuje obory názvů.</span><span class="sxs-lookup"><span data-stu-id="74936-108">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74936-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="74936-109">Return Value</span></span>  
 <span data-ttu-id="74936-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="74936-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74936-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74936-111">Requirements</span></span>  
 <span data-ttu-id="74936-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="74936-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74936-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="74936-113">See also</span></span>

- [<span data-ttu-id="74936-114">ISymUnmanagedNamespace – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74936-114">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
