---
title: "ISymUnmanagedWriter::Abort – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8013bf2118a73a8b5eb8a5b160f2655a83382efc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="27133-102">ISymUnmanagedWriter::Abort – metoda</span><span class="sxs-lookup"><span data-stu-id="27133-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="27133-103">Zavře zapisovače symbol bez potvrzení symboly pro úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="27133-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="27133-104">Po toto volání zapisovače symbol stává neplatným pro další aktualizace.</span><span class="sxs-lookup"><span data-stu-id="27133-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="27133-105">Potvrdit symboly a zavřete zapisovače symbol, použijte [isymunmanagedwriter::Close –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="27133-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27133-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27133-106">Syntax</span></span>  
  
```  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="27133-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="27133-107">Return Value</span></span>  
 <span data-ttu-id="27133-108">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="27133-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27133-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="27133-109">Requirements</span></span>  
 <span data-ttu-id="27133-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="27133-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27133-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="27133-111">See Also</span></span>  
 [<span data-ttu-id="27133-112">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="27133-112">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
