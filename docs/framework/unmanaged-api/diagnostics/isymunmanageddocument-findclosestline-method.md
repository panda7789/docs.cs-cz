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
ms.openlocfilehash: 9e6134d39096c4ab157aa545646d83339f92a0b8
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441029"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="5d8b0-102">ISymUnmanagedDocument::FindClosestLine – metoda</span><span class="sxs-lookup"><span data-stu-id="5d8b0-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>
<span data-ttu-id="5d8b0-103">Vrátí nejbližší řádek, který je sekvenčním bodem, na základě řádku v tomto dokumentu, který může nebo nemusí být bodem sekvence.</span><span class="sxs-lookup"><span data-stu-id="5d8b0-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d8b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d8b0-104">Syntax</span></span>  
  
```cpp  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d8b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d8b0-105">Parameters</span></span>  
 `line`  
 <span data-ttu-id="5d8b0-106">pro Řádek v tomto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5d8b0-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="5d8b0-107">mimo Ukazatel na proměnnou, která přijímá řádek.</span><span class="sxs-lookup"><span data-stu-id="5d8b0-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d8b0-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5d8b0-108">Return Value</span></span>  
 <span data-ttu-id="5d8b0-109">S_OK, pokud je metoda úspěšná; v opačném případě kód chyby.</span><span class="sxs-lookup"><span data-stu-id="5d8b0-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d8b0-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d8b0-110">See also</span></span>

- [<span data-ttu-id="5d8b0-111">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d8b0-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
