---
title: "ISymUnmanagedDocument::FindClosestLine – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.FindClosestLine
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8a4fff5ce5cdcde35c8483136cf4c3cd75854f6c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="0004f-102">ISymUnmanagedDocument::FindClosestLine – metoda</span><span class="sxs-lookup"><span data-stu-id="0004f-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>
<span data-ttu-id="0004f-103">Vrátí nejbližší řádek, který je bod pořadí na základě řádku v tomto dokumentu, který může nebo nemusí být bodu sekvence.</span><span class="sxs-lookup"><span data-stu-id="0004f-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0004f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0004f-104">Syntax</span></span>  
  
```  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0004f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0004f-105">Parameters</span></span>  
 `line`  
 <span data-ttu-id="0004f-106">[v] Řádek v tomto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0004f-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="0004f-107">[out] Ukazatel na proměnnou, která přijímá řádku.</span><span class="sxs-lookup"><span data-stu-id="0004f-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0004f-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0004f-108">Return Value</span></span>  
 <span data-ttu-id="0004f-109">S_OK, pokud metoda úspěšně. jinak kód chyby.</span><span class="sxs-lookup"><span data-stu-id="0004f-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0004f-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="0004f-110">See Also</span></span>  
 [<span data-ttu-id="0004f-111">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0004f-111">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
