---
title: "ISymUnmanagedWriter::DefineSequencePoints – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineSequencePoints
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 836774114798324ac16d3263e58dd56665a9aa49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="42c91-102">ISymUnmanagedWriter::DefineSequencePoints – metoda</span><span class="sxs-lookup"><span data-stu-id="42c91-102">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>
<span data-ttu-id="42c91-103">Definuje skupinu bodů pořadí v rámci aktuální metoda.</span><span class="sxs-lookup"><span data-stu-id="42c91-103">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="42c91-104">Každý počáteční řádek a počáteční sloupec definovat spuštění příkazu v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="42c91-104">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="42c91-105">Každý ukončení řádku a končí sloupec definovat konci příkazu v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="42c91-105">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="42c91-106">Pole musí být seřazeny ve vzestupném pořadí odsazení.</span><span class="sxs-lookup"><span data-stu-id="42c91-106">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="42c91-107">Posun je vždy měří od začátku metodu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="42c91-107">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42c91-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42c91-108">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="42c91-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="42c91-109">Parameters</span></span>  
 `document`  
 <span data-ttu-id="42c91-110">[v] Dokument objekt, pro které jsou definovány body sekvence.</span><span class="sxs-lookup"><span data-stu-id="42c91-110">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="42c91-111">[v] A `ULONG32` , která určuje velikost jednotlivých `offsets`, `lines`, `columns`, `endLines`, a `endColumns` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="42c91-111">[in] A `ULONG32` that that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="42c91-112">[v] Posun body sekvence se měří od začátku metody.</span><span class="sxs-lookup"><span data-stu-id="42c91-112">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="42c91-113">[v] Počáteční řádek čísla bodů pořadí.</span><span class="sxs-lookup"><span data-stu-id="42c91-113">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="42c91-114">[v] Počáteční sloupec čísla body sekvence.</span><span class="sxs-lookup"><span data-stu-id="42c91-114">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="42c91-115">[v] Koncová čísla řádků bodů pořadí.</span><span class="sxs-lookup"><span data-stu-id="42c91-115">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="42c91-116">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="42c91-116">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="42c91-117">[v] Koncová čísla sloupců body sekvence.</span><span class="sxs-lookup"><span data-stu-id="42c91-117">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="42c91-118">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="42c91-118">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42c91-119">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="42c91-119">Return Value</span></span>  
 <span data-ttu-id="42c91-120">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="42c91-120">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42c91-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42c91-121">Requirements</span></span>  
 <span data-ttu-id="42c91-122">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="42c91-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42c91-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="42c91-123">See Also</span></span>  
 [<span data-ttu-id="42c91-124">ISymUnmanagedWriter – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="42c91-124">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
