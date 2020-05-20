---
title: ISymUnmanagedMethod::GetNamespace – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetNamespace
helpviewer_keywords:
- ISymUnmanagedMethod::GetNamespace method [.NET Framework debugging]
- GetNamespace method [.NET Framework debugging]
ms.assetid: 7fbbac42-b966-406d-9ae9-67bf3aea74ce
topic_type:
- apiref
ms.openlocfilehash: cda30f3c73bf75c37ff79fc415e02382b053807e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614484"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="22972-102">ISymUnmanagedMethod::GetNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="22972-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="22972-103">Získá obor názvů, ve kterém je tato metoda definována.</span><span class="sxs-lookup"><span data-stu-id="22972-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22972-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22972-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22972-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22972-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="22972-106">mimo Ukazatel, který je nastaven na vrácené rozhraní [ISymUnmanagedNamespace](isymunmanagednamespace-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="22972-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22972-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="22972-107">Return Value</span></span>  
 <span data-ttu-id="22972-108">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="22972-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22972-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22972-109">Requirements</span></span>  
 <span data-ttu-id="22972-110">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="22972-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22972-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="22972-111">See also</span></span>

- [<span data-ttu-id="22972-112">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22972-112">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
