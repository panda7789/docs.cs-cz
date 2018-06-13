---
title: ISymUnmanagedWriter::CloseNamespace – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::CloseNamespace method [.NET Framework debugging]
- CloseNamespace method [.NET Framework debugging]
ms.assetid: 7f74d9c5-1377-4958-b842-6306d611cbd5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5d7e1e4da51445a55387b813e814183bf7433e45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426920"
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="53538-102">ISymUnmanagedWriter::CloseNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="53538-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>
<span data-ttu-id="53538-103">Zavře naposledy Otevřít obor názvů.</span><span class="sxs-lookup"><span data-stu-id="53538-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53538-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53538-104">Syntax</span></span>  
  
```  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="53538-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="53538-105">Return Value</span></span>  
 <span data-ttu-id="53538-106">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="53538-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53538-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="53538-107">Requirements</span></span>  
 <span data-ttu-id="53538-108">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="53538-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53538-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="53538-109">See Also</span></span>  
 [<span data-ttu-id="53538-110">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="53538-110">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="53538-111">OpenNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="53538-111">OpenNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)
