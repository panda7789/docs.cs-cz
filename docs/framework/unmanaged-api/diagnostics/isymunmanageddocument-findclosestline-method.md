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
ms.openlocfilehash: ab7df9b77b1820f291c1b1873b4dfb39e326bc34
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193158"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="cbb89-102">ISymUnmanagedDocument::FindClosestLine – metoda</span><span class="sxs-lookup"><span data-stu-id="cbb89-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>
<span data-ttu-id="cbb89-103">Vrátí nejbližší řádek, který je bodu sekvence. Zadaný řádek v tomto dokumentu, který může nebo nemusí být bodu sekvence.</span><span class="sxs-lookup"><span data-stu-id="cbb89-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbb89-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbb89-104">Syntax</span></span>  
  
```  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbb89-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cbb89-105">Parameters</span></span>  
 `line`  
 <span data-ttu-id="cbb89-106">[in] Řádek v tomto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="cbb89-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="cbb89-107">[out] Ukazovat na proměnnou, která přijímá řádku.</span><span class="sxs-lookup"><span data-stu-id="cbb89-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cbb89-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cbb89-108">Return Value</span></span>  
 <span data-ttu-id="cbb89-109">Pokud metoda uspěje; S_OK v opačném případě chybový kód.</span><span class="sxs-lookup"><span data-stu-id="cbb89-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbb89-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cbb89-110">See also</span></span>

- [<span data-ttu-id="cbb89-111">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cbb89-111">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
