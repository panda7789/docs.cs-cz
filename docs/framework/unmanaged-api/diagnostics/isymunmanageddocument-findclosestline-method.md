---
title: ISymUnmanagedDocument::FindClosestLine – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.FindClosestLine
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f31dad53f42fdd8f7ac3a0cb995b507ecc3590d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424440"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="76556-102">ISymUnmanagedDocument::FindClosestLine – metoda</span><span class="sxs-lookup"><span data-stu-id="76556-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>
<span data-ttu-id="76556-103">Vrátí nejbližší řádek, který je bod pořadí na základě řádku v tomto dokumentu, který může nebo nemusí být bodu sekvence.</span><span class="sxs-lookup"><span data-stu-id="76556-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76556-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76556-104">Syntax</span></span>  
  
```  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76556-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="76556-105">Parameters</span></span>  
 `line`  
 <span data-ttu-id="76556-106">[v] Řádek v tomto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="76556-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="76556-107">[out] Ukazatel na proměnnou, která přijímá řádku.</span><span class="sxs-lookup"><span data-stu-id="76556-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76556-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="76556-108">Return Value</span></span>  
 <span data-ttu-id="76556-109">S_OK, pokud metoda úspěšně. jinak kód chyby.</span><span class="sxs-lookup"><span data-stu-id="76556-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76556-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="76556-110">See Also</span></span>  
 [<span data-ttu-id="76556-111">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="76556-111">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
