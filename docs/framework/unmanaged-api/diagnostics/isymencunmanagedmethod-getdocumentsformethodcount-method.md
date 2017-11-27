---
title: "ISymENCUnmanagedMethod::GetDocumentsForMethodCount – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetDocumentsForMethodCount
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetDocumentsForMethodCount
helpviewer_keywords:
- GetDocumentsForMethodCount method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount method [.NET Framework debugging]
ms.assetid: cc1a823a-3ff3-4a33-b641-96edc93d2b17
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 49b849ced80d526ed529bad1eaa766d5a2a19d51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymencunmanagedmethodgetdocumentsformethodcount-method"></a><span data-ttu-id="04376-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount – metoda</span><span class="sxs-lookup"><span data-stu-id="04376-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Method</span></span>
<span data-ttu-id="04376-103">Získá počet dokumentů, které tato metoda má řádky v.</span><span class="sxs-lookup"><span data-stu-id="04376-103">Gets the number of documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04376-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04376-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentsForMethodCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04376-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04376-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="04376-106">[out] Ukazatel na `ULONG32` která přijme velikost vyrovnávací paměti musí obsahovat dokumenty.</span><span class="sxs-lookup"><span data-stu-id="04376-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04376-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="04376-107">Return Value</span></span>  
 <span data-ttu-id="04376-108">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="04376-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04376-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04376-109">Requirements</span></span>  
 <span data-ttu-id="04376-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="04376-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04376-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="04376-111">See Also</span></span>  
 [<span data-ttu-id="04376-112">Isymencunmanagedmethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04376-112">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
