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
ms.openlocfilehash: 8d6be64137b59c84dfadbd7f0e4895eac2fb27e4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776796"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="00e0e-102">ISymUnmanagedDocument::FindClosestLine – metoda</span><span class="sxs-lookup"><span data-stu-id="00e0e-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>
<span data-ttu-id="00e0e-103">Vrátí nejbližší řádek, který je bodu sekvence. Zadaný řádek v tomto dokumentu, který může nebo nemusí být bodu sekvence.</span><span class="sxs-lookup"><span data-stu-id="00e0e-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00e0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00e0e-104">Syntax</span></span>  
  
```cpp  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00e0e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00e0e-105">Parameters</span></span>  
 `line`  
 <span data-ttu-id="00e0e-106">[in] Řádek v tomto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="00e0e-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="00e0e-107">[out] Ukazovat na proměnnou, která přijímá řádku.</span><span class="sxs-lookup"><span data-stu-id="00e0e-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00e0e-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="00e0e-108">Return Value</span></span>  
 <span data-ttu-id="00e0e-109">Pokud metoda uspěje; S_OK v opačném případě chybový kód.</span><span class="sxs-lookup"><span data-stu-id="00e0e-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00e0e-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00e0e-110">See also</span></span>

- [<span data-ttu-id="00e0e-111">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00e0e-111">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
