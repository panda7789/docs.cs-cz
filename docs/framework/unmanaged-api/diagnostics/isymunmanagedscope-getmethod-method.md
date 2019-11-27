---
title: ISymUnmanagedScope::GetMethod – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetMethod method [.NET Framework debugging]
ms.assetid: a61866ee-221a-45b9-a1b7-395825b77872
topic_type:
- apiref
ms.openlocfilehash: 348a8cebe0fd746f3ae490484ffcca2fcb77684b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446311"
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="a4b3a-102">ISymUnmanagedScope::GetMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="a4b3a-102">ISymUnmanagedScope::GetMethod Method</span></span>
<span data-ttu-id="a4b3a-103">Získá metodu, která obsahuje tento obor.</span><span class="sxs-lookup"><span data-stu-id="a4b3a-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4b3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4b3a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4b3a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4b3a-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a4b3a-106">mimo Ukazatel na vrácené rozhraní [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a4b3a-106">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4b3a-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a4b3a-107">Return Value</span></span>  
 <span data-ttu-id="a4b3a-108">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="a4b3a-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4b3a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a4b3a-109">Requirements</span></span>  
 <span data-ttu-id="a4b3a-110">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a4b3a-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4b3a-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4b3a-111">See also</span></span>

- [<span data-ttu-id="a4b3a-112">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a4b3a-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
