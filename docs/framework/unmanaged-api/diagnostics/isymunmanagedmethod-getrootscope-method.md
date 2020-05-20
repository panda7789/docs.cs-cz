---
title: ISymUnmanagedMethod::GetRootScope – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRootScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRootScope
helpviewer_keywords:
- ISymUnmanagedMethod::GetRootScope method [.NET Framework debugging]
- GetRootScope method [.NET Framework debugging]
ms.assetid: 7d58caac-2e75-4dfa-9249-32d8a624b247
topic_type:
- apiref
ms.openlocfilehash: 650a64e72b410cddfbee7dce676ddbb5a3b8b3d3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614445"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="d15c6-102">ISymUnmanagedMethod::GetRootScope – metoda</span><span class="sxs-lookup"><span data-stu-id="d15c6-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="d15c6-103">Získá kořenový lexikální rozsah v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="d15c6-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="d15c6-104">Tento obor uzavírá celou metodu.</span><span class="sxs-lookup"><span data-stu-id="d15c6-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d15c6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d15c6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d15c6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d15c6-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="d15c6-107">mimo Ukazatel, který je nastaven na vrácené rozhraní [ISymUnmanagedScope](isymunmanagedscope-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d15c6-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d15c6-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d15c6-108">Return Value</span></span>  
 <span data-ttu-id="d15c6-109">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="d15c6-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d15c6-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d15c6-110">Requirements</span></span>  
 <span data-ttu-id="d15c6-111">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d15c6-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d15c6-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="d15c6-112">See also</span></span>

- [<span data-ttu-id="d15c6-113">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d15c6-113">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
