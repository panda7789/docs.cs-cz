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
ms.openlocfilehash: 7a4ffc0c417ae839e5c97ffe6884bc3230a603b7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610103"
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="4ebd9-102">ISymUnmanagedWriter::CloseNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="4ebd9-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>
<span data-ttu-id="4ebd9-103">Zavře naposledy otevřený obor názvů.</span><span class="sxs-lookup"><span data-stu-id="4ebd9-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ebd9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ebd9-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4ebd9-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4ebd9-105">Return Value</span></span>  
 <span data-ttu-id="4ebd9-106">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="4ebd9-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ebd9-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4ebd9-107">Requirements</span></span>  
 <span data-ttu-id="4ebd9-108">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4ebd9-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ebd9-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ebd9-109">See also</span></span>

- [<span data-ttu-id="4ebd9-110">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4ebd9-110">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="4ebd9-111">OpenNamespace – metoda</span><span class="sxs-lookup"><span data-stu-id="4ebd9-111">OpenNamespace Method</span></span>](isymunmanagedwriter-opennamespace-method.md)
