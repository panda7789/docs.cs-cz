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
ms.openlocfilehash: 09f39d3b6486e2ec3c04c5d1858a85ce56895527
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610155"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="23856-102">ISymUnmanagedWriter::Abort – metoda</span><span class="sxs-lookup"><span data-stu-id="23856-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="23856-103">Zavře zapisovač symbolů bez potvrzení symbolů do úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="23856-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="23856-104">Po tomto volání bude zapisovač symbolů pro další aktualizace neplatný.</span><span class="sxs-lookup"><span data-stu-id="23856-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="23856-105">Chcete-li symboly potvrdit a zavřít zapisovač symbolů, použijte místo toho metodu [ISymUnmanagedWriter:: Close](isymunmanagedwriter-close-method.md) .</span><span class="sxs-lookup"><span data-stu-id="23856-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23856-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23856-106">Syntax</span></span>  
  
```cpp  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="23856-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="23856-107">Return Value</span></span>  
 <span data-ttu-id="23856-108">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="23856-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23856-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="23856-109">Requirements</span></span>  
 <span data-ttu-id="23856-110">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="23856-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23856-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="23856-111">See also</span></span>

- [<span data-ttu-id="23856-112">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="23856-112">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
