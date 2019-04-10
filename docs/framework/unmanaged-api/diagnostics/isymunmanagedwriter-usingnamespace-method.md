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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d0739cc38d1f12967f0daef2d6828e04a256ade6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201842"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="56f58-102">ISymUnmanagedWriter::UsingNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="56f58-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>
<span data-ttu-id="56f58-103">Určuje, že daný plně kvalifikovaný obor názvů je používán v rámci oboru lexikální aktuálně otevřené.</span><span class="sxs-lookup"><span data-stu-id="56f58-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="56f58-104">Obor názvů se použije v rámci všechny obory, které dědí z oboru aktuálně otevřené.</span><span class="sxs-lookup"><span data-stu-id="56f58-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="56f58-105">Zavření aktuálního oboru se zastaví také použití oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="56f58-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56f58-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56f58-106">Syntax</span></span>  
  
```  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56f58-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="56f58-107">Parameters</span></span>  
 `fullName`  
 <span data-ttu-id="56f58-108">[in] Ukazatel na plně kvalifikovaný název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="56f58-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56f58-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="56f58-109">Return Value</span></span>  
 <span data-ttu-id="56f58-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="56f58-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56f58-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56f58-111">Requirements</span></span>  
 <span data-ttu-id="56f58-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="56f58-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56f58-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56f58-113">See also</span></span>

- [<span data-ttu-id="56f58-114">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56f58-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
