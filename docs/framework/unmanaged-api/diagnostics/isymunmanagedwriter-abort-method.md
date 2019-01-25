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
ms.openlocfilehash: b4c79cb3df37a9ed10e46567be63aad29fee37c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550185"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="6a999-102">ISymUnmanagedWriter::Abort – metoda</span><span class="sxs-lookup"><span data-stu-id="6a999-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="6a999-103">Zavře zapisovač symbol bez potvrzení symbolů do úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="6a999-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="6a999-104">Po tomto volání zapisovač symbol stává neplatným další aktualizace.</span><span class="sxs-lookup"><span data-stu-id="6a999-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="6a999-105">Chcete-li potvrdit symboly a zavřít zapisovač symbol, použijte [isymunmanagedwriter::Close –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) metoda místo toho.</span><span class="sxs-lookup"><span data-stu-id="6a999-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a999-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a999-106">Syntax</span></span>  
  
```  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6a999-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6a999-107">Return Value</span></span>  
 <span data-ttu-id="6a999-108">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="6a999-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a999-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a999-109">Requirements</span></span>  
 <span data-ttu-id="6a999-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6a999-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a999-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a999-111">See also</span></span>
- [<span data-ttu-id="6a999-112">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a999-112">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
