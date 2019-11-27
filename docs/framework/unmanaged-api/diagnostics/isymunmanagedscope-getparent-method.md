---
title: ISymUnmanagedScope::GetParent – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetParent
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetParent
helpviewer_keywords:
- GetParent method [.NET Framework debugging]
- ISymUnmanagedScope::GetParent method [.NET Framework debugging]
ms.assetid: c7963c87-6ec5-49b3-a5cd-e0fe0c43f9b4
topic_type:
- apiref
ms.openlocfilehash: 512dd4055a0aad8498db6ef2241c9363aecee9c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446287"
---
# <a name="isymunmanagedscopegetparent-method"></a><span data-ttu-id="4daba-102">ISymUnmanagedScope::GetParent – metoda</span><span class="sxs-lookup"><span data-stu-id="4daba-102">ISymUnmanagedScope::GetParent Method</span></span>
<span data-ttu-id="4daba-103">Získá nadřazený obor tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="4daba-103">Gets the parent scope of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4daba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4daba-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParent(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4daba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4daba-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="4daba-106">mimo Ukazatel na vrácené rozhraní [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="4daba-106">[out] A pointer to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4daba-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4daba-107">Return Value</span></span>  
 <span data-ttu-id="4daba-108">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="4daba-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4daba-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4daba-109">Requirements</span></span>  
 <span data-ttu-id="4daba-110">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4daba-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4daba-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4daba-111">See also</span></span>

- [<span data-ttu-id="4daba-112">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4daba-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="4daba-113">GetChildren – metoda</span><span class="sxs-lookup"><span data-stu-id="4daba-113">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)
