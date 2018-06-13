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
ms.openlocfilehash: 32036058924aaf79fa7282144ced75040bc1f825
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426017"
---
# <a name="isymunmanagedmethodgetranges-method"></a><span data-ttu-id="dceff-102">ISymUnmanagedMethod::GetRanges – metoda</span><span class="sxs-lookup"><span data-stu-id="dceff-102">ISymUnmanagedMethod::GetRanges Method</span></span>
<span data-ttu-id="dceff-103">Dané pozici v dokumentu vrátí pole počáteční a koncové posunutí párů, které odpovídají na rozsahy Microsoft (MSIL intermediate language) pokrývající pozici v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="dceff-103">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span> <span data-ttu-id="dceff-104">Toto pole je pole celých čísel a má formát [start, end, spuštění, koncové].</span><span class="sxs-lookup"><span data-stu-id="dceff-104">The array is an array of integers and has the format [start, end, start, end].</span></span> <span data-ttu-id="dceff-105">Počet dvojic rozsah je délka pole dělený 2.</span><span class="sxs-lookup"><span data-stu-id="dceff-105">The number of range pairs is the length of the array divided by 2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dceff-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dceff-106">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="dceff-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="dceff-107">Parameters</span></span>  
 `document`  
 <span data-ttu-id="dceff-108">[v] Dokument, pro které je požadováno posun.</span><span class="sxs-lookup"><span data-stu-id="dceff-108">[in] The document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="dceff-109">[v] Dokument řádku odpovídající rozsahy.</span><span class="sxs-lookup"><span data-stu-id="dceff-109">[in] The document line corresponding to the ranges.</span></span>  
  
 `column`  
 <span data-ttu-id="dceff-110">[v] Sloupec dokumentu odpovídající rozsahy.</span><span class="sxs-lookup"><span data-stu-id="dceff-110">[in] The document column corresponding to the ranges.</span></span>  
  
 `cRanges`  
 <span data-ttu-id="dceff-111">[v] Velikost `ranges` pole.</span><span class="sxs-lookup"><span data-stu-id="dceff-111">[in] The size of the `ranges` array.</span></span>  
  
 `pcRanges`  
 <span data-ttu-id="dceff-112">[out] Ukazatel na `ULONG32` která přijme velikost vyrovnávací paměti musí obsahovat rozsahy.</span><span class="sxs-lookup"><span data-stu-id="dceff-112">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span></span>  
  
 `ranges`  
 <span data-ttu-id="dceff-113">[out] Ukazatel do vyrovnávací paměti, která přijímá rozsahy.</span><span class="sxs-lookup"><span data-stu-id="dceff-113">[out] A pointer to the buffer that receives the ranges.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dceff-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dceff-114">Return Value</span></span>  
 <span data-ttu-id="dceff-115">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="dceff-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dceff-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dceff-116">Requirements</span></span>  
 <span data-ttu-id="dceff-117">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="dceff-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dceff-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="dceff-118">See Also</span></span>  
 [<span data-ttu-id="dceff-119">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dceff-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
