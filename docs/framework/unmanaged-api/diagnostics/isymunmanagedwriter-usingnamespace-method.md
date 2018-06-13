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
ms.openlocfilehash: 9a5ff52a95fd6ebaec05439cbc702d5513d0cc78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427766"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="e9247-102">ISymUnmanagedWriter::UsingNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="e9247-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>
<span data-ttu-id="e9247-103">Určuje, že zadaný obor názvů plně kvalifikovaný název je používán v rámci oboru lexikální aktuálně otevřené.</span><span class="sxs-lookup"><span data-stu-id="e9247-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="e9247-104">Obor názvů se použije v rámci všechny obory, které dědí z aktuálně otevřených oboru.</span><span class="sxs-lookup"><span data-stu-id="e9247-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="e9247-105">Zavření v aktuálním oboru také zastaví použití oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e9247-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9247-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9247-106">Syntax</span></span>  
  
```  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9247-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9247-107">Parameters</span></span>  
 `fullName`  
 <span data-ttu-id="e9247-108">[v] Ukazatel na plně kvalifikovaný název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e9247-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9247-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e9247-109">Return Value</span></span>  
 <span data-ttu-id="e9247-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="e9247-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9247-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e9247-111">Requirements</span></span>  
 <span data-ttu-id="e9247-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e9247-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9247-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9247-113">See Also</span></span>  
 [<span data-ttu-id="e9247-114">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e9247-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
