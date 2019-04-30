---
title: ISymENCUnmanagedMethod::GetDocumentsForMethodCount – metoda
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethodCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount
helpviewer_keywords:
- GetDocumentsForMethodCount method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount method [.NET Framework debugging]
ms.assetid: cc1a823a-3ff3-4a33-b641-96edc93d2b17
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef1b8dce5c84382a9039787d2205f1ac8ccbc5bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940280"
---
# <a name="isymencunmanagedmethodgetdocumentsformethodcount-method"></a><span data-ttu-id="d0324-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount – metoda</span><span class="sxs-lookup"><span data-stu-id="d0324-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Method</span></span>
<span data-ttu-id="d0324-103">Získá počet dokumentů, které tato metoda má řádky v.</span><span class="sxs-lookup"><span data-stu-id="d0324-103">Gets the number of documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0324-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0324-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentsForMethodCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0324-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0324-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="d0324-106">[out] Ukazatel `ULONG32` , která obdrží velikost vyrovnávací paměti musí obsahovat dokumenty.</span><span class="sxs-lookup"><span data-stu-id="d0324-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0324-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d0324-107">Return Value</span></span>  
 <span data-ttu-id="d0324-108">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="d0324-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0324-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0324-109">Requirements</span></span>  
 <span data-ttu-id="d0324-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d0324-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0324-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0324-111">See also</span></span>

- [<span data-ttu-id="d0324-112">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0324-112">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
