---
title: ISymUnmanagedWriter::DefineSequencePoints – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 735b33ac1f049f8d4d3740239e7c34a6fa16dd32
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146936"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="da4aa-102">ISymUnmanagedWriter::DefineSequencePoints – metoda</span><span class="sxs-lookup"><span data-stu-id="da4aa-102">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>
<span data-ttu-id="da4aa-103">Definuje skupinu pořadí bodů v aktuální metodě.</span><span class="sxs-lookup"><span data-stu-id="da4aa-103">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="da4aa-104">Každé počáteční řádek a počáteční sloupec definovat spuštění příkazu v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="da4aa-104">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="da4aa-105">Každý ukončení řádku a poslední sloupec definovat konec příkazu v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="da4aa-105">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="da4aa-106">Tato pole mají být řazeny ve vzestupném pořadí podle posunů.</span><span class="sxs-lookup"><span data-stu-id="da4aa-106">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="da4aa-107">Posun je vždy prováděno od samého začátku metody v bajtech.</span><span class="sxs-lookup"><span data-stu-id="da4aa-107">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da4aa-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da4aa-108">Syntax</span></span>  
  
```  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da4aa-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="da4aa-109">Parameters</span></span>  
 `document`  
 <span data-ttu-id="da4aa-110">[in] Objekt dokumentu, pro které jsou definovány body sekvence.</span><span class="sxs-lookup"><span data-stu-id="da4aa-110">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="da4aa-111">[in] A `ULONG32` , který označuje velikost jednotlivých `offsets`, `lines`, `columns`, `endLines`, a `endColumns` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="da4aa-111">[in] A `ULONG32` that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="da4aa-112">[in] Posun body sekvence měřená od začátku metody.</span><span class="sxs-lookup"><span data-stu-id="da4aa-112">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="da4aa-113">[in] Počáteční řádek čísla body sekvence.</span><span class="sxs-lookup"><span data-stu-id="da4aa-113">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="da4aa-114">[in] Počáteční sloupec čísla body sekvence.</span><span class="sxs-lookup"><span data-stu-id="da4aa-114">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="da4aa-115">[in] Koncového čísla řádku body sekvence.</span><span class="sxs-lookup"><span data-stu-id="da4aa-115">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="da4aa-116">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="da4aa-116">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="da4aa-117">[in] Koncového čísla sloupce body sekvence.</span><span class="sxs-lookup"><span data-stu-id="da4aa-117">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="da4aa-118">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="da4aa-118">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da4aa-119">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="da4aa-119">Return Value</span></span>  
 <span data-ttu-id="da4aa-120">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="da4aa-120">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da4aa-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da4aa-121">Requirements</span></span>  
 <span data-ttu-id="da4aa-122">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="da4aa-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da4aa-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da4aa-123">See also</span></span>

- [<span data-ttu-id="da4aa-124">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da4aa-124">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
