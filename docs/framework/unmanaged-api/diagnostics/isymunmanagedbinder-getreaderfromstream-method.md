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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 21e147860c6859ea23409de31fed972c4f2bb432
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940072"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="de8b7-102">ISymUnmanagedBinder::GetReaderFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="de8b7-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>
<span data-ttu-id="de8b7-103">Rozhraní metadat a datový proud, který obsahuje úložiště symbolů, vrátí správné [isymunmanagedreader –](isymunmanagedreader-interface.md) struktura, která bude číst ladění symboly z úložiště daného symbolu.</span><span class="sxs-lookup"><span data-stu-id="de8b7-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de8b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de8b7-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de8b7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="de8b7-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="de8b7-106">[in] Ukazatel na rozhraní import metadat.</span><span class="sxs-lookup"><span data-stu-id="de8b7-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="de8b7-107">[in] Ukazatel na datový proud, který obsahuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="de8b7-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="de8b7-108">[out] Ukazatel, který je nastaven na vrácenou [isymunmanagedreader –](isymunmanagedreader-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="de8b7-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de8b7-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="de8b7-109">Return Value</span></span>  
 <span data-ttu-id="de8b7-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="de8b7-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de8b7-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="de8b7-111">Requirements</span></span>  
 <span data-ttu-id="de8b7-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="de8b7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de8b7-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de8b7-113">See also</span></span>

- [<span data-ttu-id="de8b7-114">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="de8b7-114">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
