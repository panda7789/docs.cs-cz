---
title: ISymUnmanagedWriter::UsingNamespace – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.UsingNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type:
- apiref
ms.openlocfilehash: cb0af78092822875204f45ec3dca1484e5b5fc90
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427466"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="5c860-102">ISymUnmanagedWriter::UsingNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="5c860-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>
<span data-ttu-id="5c860-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span><span class="sxs-lookup"><span data-stu-id="5c860-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="5c860-104">The namespace will be used within all scopes that inherit from the currently open scope.</span><span class="sxs-lookup"><span data-stu-id="5c860-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="5c860-105">Closing the current scope will also stop the use of the namespace.</span><span class="sxs-lookup"><span data-stu-id="5c860-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c860-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c860-106">Syntax</span></span>  
  
```cpp  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c860-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c860-107">Parameters</span></span>  
 `fullName`  
 <span data-ttu-id="5c860-108">[in] A pointer to the fully qualified name of the namespace.</span><span class="sxs-lookup"><span data-stu-id="5c860-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c860-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5c860-109">Return Value</span></span>  
 <span data-ttu-id="5c860-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="5c860-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c860-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5c860-111">Requirements</span></span>  
 <span data-ttu-id="5c860-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5c860-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c860-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c860-113">See also</span></span>

- [<span data-ttu-id="5c860-114">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c860-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
