---
title: ISymUnmanagedWriter::Abort – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Abort
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb6a3e65b1f1d59cde3bff99e491bcf09816c8ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428055"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="fb665-102">ISymUnmanagedWriter::Abort – metoda</span><span class="sxs-lookup"><span data-stu-id="fb665-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="fb665-103">Zavře zapisovače symbol bez potvrzení symboly pro úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="fb665-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="fb665-104">Po toto volání zapisovače symbol stává neplatným pro další aktualizace.</span><span class="sxs-lookup"><span data-stu-id="fb665-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="fb665-105">Potvrdit symboly a zavřete zapisovače symbol, použijte [isymunmanagedwriter::Close –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="fb665-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb665-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb665-106">Syntax</span></span>  
  
```  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fb665-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fb665-107">Return Value</span></span>  
 <span data-ttu-id="fb665-108">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="fb665-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb665-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb665-109">Requirements</span></span>  
 <span data-ttu-id="fb665-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fb665-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb665-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb665-111">See Also</span></span>  
 [<span data-ttu-id="fb665-112">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb665-112">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
