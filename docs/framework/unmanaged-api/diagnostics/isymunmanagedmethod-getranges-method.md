---
title: ISymUnmanagedMethod::GetRanges – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRanges
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRanges
helpviewer_keywords:
- ISymUnmanagedMethod::GetRanges method [.NET Framework debugging]
- GetRanges method [.NET Framework debugging]
ms.assetid: a85283d8-379c-417a-9736-ddeeef9bcf50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 308207e100a9770474dd896ea4cba42d7db5d241
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485548"
---
# <a name="isymunmanagedmethodgetranges-method"></a><span data-ttu-id="e1917-102">ISymUnmanagedMethod::GetRanges – metoda</span><span class="sxs-lookup"><span data-stu-id="e1917-102">ISymUnmanagedMethod::GetRanges Method</span></span>
<span data-ttu-id="e1917-103">Danou pozici v dokumentu vrátí pole dvojic počáteční a koncové posunutí, které odpovídají na rozsahy jazyk Microsoft intermediate language (MSIL), která zahrnuje pozici v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="e1917-103">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span> <span data-ttu-id="e1917-104">Pole je pole celých čísel a má formát [spuštění, end, zahájení, ukončení].</span><span class="sxs-lookup"><span data-stu-id="e1917-104">The array is an array of integers and has the format [start, end, start, end].</span></span> <span data-ttu-id="e1917-105">Počet dvojic rozsah je délka pole, děleno 2.</span><span class="sxs-lookup"><span data-stu-id="e1917-105">The number of range pairs is the length of the array divided by 2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1917-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1917-106">Syntax</span></span>  
  
```  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1917-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1917-107">Parameters</span></span>  
 `document`  
 <span data-ttu-id="e1917-108">[in] Dokument, pro kterou je požadována posun.</span><span class="sxs-lookup"><span data-stu-id="e1917-108">[in] The document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="e1917-109">[in] Dokument řádek odpovídající oblasti.</span><span class="sxs-lookup"><span data-stu-id="e1917-109">[in] The document line corresponding to the ranges.</span></span>  
  
 `column`  
 <span data-ttu-id="e1917-110">[in] Sloupec dokumentu odpovídající oblasti.</span><span class="sxs-lookup"><span data-stu-id="e1917-110">[in] The document column corresponding to the ranges.</span></span>  
  
 `cRanges`  
 <span data-ttu-id="e1917-111">[in] Velikost `ranges` pole.</span><span class="sxs-lookup"><span data-stu-id="e1917-111">[in] The size of the `ranges` array.</span></span>  
  
 `pcRanges`  
 <span data-ttu-id="e1917-112">[out] Ukazatel `ULONG32` , která obdrží velikost vyrovnávací paměti musí obsahovat rozsahy.</span><span class="sxs-lookup"><span data-stu-id="e1917-112">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span></span>  
  
 `ranges`  
 <span data-ttu-id="e1917-113">[out] Ukazatel do vyrovnávací paměti, která přijímá rozsahů.</span><span class="sxs-lookup"><span data-stu-id="e1917-113">[out] A pointer to the buffer that receives the ranges.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1917-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e1917-114">Return Value</span></span>  
 <span data-ttu-id="e1917-115">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="e1917-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1917-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e1917-116">Requirements</span></span>  
 <span data-ttu-id="e1917-117">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e1917-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1917-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1917-118">See also</span></span>
- [<span data-ttu-id="e1917-119">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e1917-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
