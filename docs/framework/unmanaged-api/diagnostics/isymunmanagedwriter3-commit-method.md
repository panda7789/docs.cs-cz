---
title: ISymUnmanagedWriter3::Commit – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.Commit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::Commit
helpviewer_keywords:
- Commit method, ISymUnmanagedWriter3 interface [.NET Framework debugging]
- ISymUnmanagedWriter3::Commit method [.NET Framework debugging]
ms.assetid: f6961922-46ec-4d2c-8369-85f880731f37
topic_type:
- apiref
ms.openlocfilehash: 4331728a4766d81b723c439747e5e1181815394f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614666"
---
# <a name="isymunmanagedwriter3commit-method"></a><span data-ttu-id="be82d-102">ISymUnmanagedWriter3::Commit – metoda</span><span class="sxs-lookup"><span data-stu-id="be82d-102">ISymUnmanagedWriter3::Commit Method</span></span>
<span data-ttu-id="be82d-103">Potvrdí změny, které byly doposud napsány do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="be82d-103">Commits the changes written so far to the stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be82d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be82d-104">Syntax</span></span>  
  
```cpp  
HRESULT Commit();  
```  
  
## <a name="return-value"></a><span data-ttu-id="be82d-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="be82d-105">Return Value</span></span>  
 <span data-ttu-id="be82d-106">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="be82d-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be82d-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be82d-107">Requirements</span></span>  
 <span data-ttu-id="be82d-108">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="be82d-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be82d-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="be82d-109">See also</span></span>

- [<span data-ttu-id="be82d-110">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be82d-110">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
