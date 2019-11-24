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
ms.openlocfilehash: da2906187c02bbc7a35c937663e3fc7db1ebda13
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433895"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="73a61-102">ISymUnmanagedNamespace::GetNamespaces – metoda</span><span class="sxs-lookup"><span data-stu-id="73a61-102">ISymUnmanagedNamespace::GetNamespaces Method</span></span>
<span data-ttu-id="73a61-103">Gets the children of this namespace.</span><span class="sxs-lookup"><span data-stu-id="73a61-103">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73a61-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73a61-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73a61-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73a61-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="73a61-106">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span><span class="sxs-lookup"><span data-stu-id="73a61-106">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="73a61-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span><span class="sxs-lookup"><span data-stu-id="73a61-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="73a61-108">[out] A pointer to the buffer that contains the namespaces.</span><span class="sxs-lookup"><span data-stu-id="73a61-108">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73a61-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="73a61-109">Return Value</span></span>  
 <span data-ttu-id="73a61-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="73a61-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73a61-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73a61-111">Requirements</span></span>  
 <span data-ttu-id="73a61-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="73a61-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73a61-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73a61-113">See also</span></span>

- [<span data-ttu-id="73a61-114">ISymUnmanagedNamespace – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73a61-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
