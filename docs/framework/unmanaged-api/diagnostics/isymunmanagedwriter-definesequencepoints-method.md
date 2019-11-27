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
ms.openlocfilehash: 63ba108bc234e566450bb019afc63acb4e75ad1f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427980"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="ab79b-102">ISymUnmanagedWriter::DefineSequencePoints – metoda</span><span class="sxs-lookup"><span data-stu-id="ab79b-102">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>
<span data-ttu-id="ab79b-103">Definuje skupinu bodů sekvence v rámci aktuální metody.</span><span class="sxs-lookup"><span data-stu-id="ab79b-103">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="ab79b-104">Každý počáteční řádek a počáteční sloupec definují začátek příkazu v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="ab79b-104">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="ab79b-105">Každý koncový řádek a koncový sloupec definují konec příkazu v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="ab79b-105">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="ab79b-106">Pole by se měla seřadit ve vzestupném pořadí posunů.</span><span class="sxs-lookup"><span data-stu-id="ab79b-106">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="ab79b-107">Posun je vždy měřen od začátku metody (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="ab79b-107">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab79b-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab79b-108">Syntax</span></span>  
  
```cpp  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab79b-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab79b-109">Parameters</span></span>  
 `document`  
 <span data-ttu-id="ab79b-110">pro Objekt dokumentu, pro který jsou definovány body sekvence.</span><span class="sxs-lookup"><span data-stu-id="ab79b-110">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="ab79b-111">pro `ULONG32`, která indikuje velikost každé `offsets`, `lines`, `columns`, `endLines`a `endColumns` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ab79b-111">[in] A `ULONG32` that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="ab79b-112">pro Posun bodů sekvence měřený od začátku metody</span><span class="sxs-lookup"><span data-stu-id="ab79b-112">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="ab79b-113">pro Počáteční čísla řádků bodů sekvence.</span><span class="sxs-lookup"><span data-stu-id="ab79b-113">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="ab79b-114">pro Čísla počátečních sloupců bodů sekvence</span><span class="sxs-lookup"><span data-stu-id="ab79b-114">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="ab79b-115">pro Koncová čísla řádků bodů sekvence.</span><span class="sxs-lookup"><span data-stu-id="ab79b-115">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="ab79b-116">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="ab79b-116">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="ab79b-117">pro Čísla koncových sloupců bodů sekvence.</span><span class="sxs-lookup"><span data-stu-id="ab79b-117">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="ab79b-118">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="ab79b-118">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab79b-119">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ab79b-119">Return Value</span></span>  
 <span data-ttu-id="ab79b-120">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="ab79b-120">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab79b-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab79b-121">Requirements</span></span>  
 <span data-ttu-id="ab79b-122">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ab79b-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab79b-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab79b-123">See also</span></span>

- [<span data-ttu-id="ab79b-124">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab79b-124">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
