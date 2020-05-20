---
title: ISymUnmanagedBinder::GetReaderFromStream – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderFromStream
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type:
- apiref
ms.openlocfilehash: 351bb2a1eb03684a0498fba35270e1bda44a93c0
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441744"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="d709e-102">ISymUnmanagedBinder::GetReaderFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="d709e-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>
<span data-ttu-id="d709e-103">Vzhledem k rozhraní metadat a datovému proudu, který obsahuje úložiště symbolů, vrátí správnou strukturu [ISymUnmanagedReader](isymunmanagedreader-interface.md) , která načte symboly ladění z daného úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="d709e-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d709e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d709e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d709e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d709e-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="d709e-106">pro Ukazatel na rozhraní pro import metadat.</span><span class="sxs-lookup"><span data-stu-id="d709e-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="d709e-107">pro Ukazatel na datový proud, který obsahuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="d709e-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="d709e-108">mimo Ukazatel, který je nastaven na vrácené rozhraní [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d709e-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d709e-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d709e-109">Return Value</span></span>  
 <span data-ttu-id="d709e-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="d709e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d709e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d709e-111">Requirements</span></span>  
 <span data-ttu-id="d709e-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d709e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d709e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d709e-113">See also</span></span>

- [<span data-ttu-id="d709e-114">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d709e-114">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
