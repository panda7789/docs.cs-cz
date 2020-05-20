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
ms.openlocfilehash: 8889c412f414f38d1d18d33ec297e82fd052280d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614796"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="b6633-102">ISymUnmanagedWriter::DefineSequencePoints – metoda</span><span class="sxs-lookup"><span data-stu-id="b6633-102">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>
<span data-ttu-id="b6633-103">Definuje skupinu bodů sekvence v rámci aktuální metody.</span><span class="sxs-lookup"><span data-stu-id="b6633-103">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="b6633-104">Každý počáteční řádek a počáteční sloupec definují začátek příkazu v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="b6633-104">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="b6633-105">Každý koncový řádek a koncový sloupec definují konec příkazu v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="b6633-105">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="b6633-106">Pole by se měla seřadit ve vzestupném pořadí posunů.</span><span class="sxs-lookup"><span data-stu-id="b6633-106">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="b6633-107">Posun je vždy měřen od začátku metody (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="b6633-107">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6633-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6633-108">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b6633-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6633-109">Parameters</span></span>  
 `document`  
 <span data-ttu-id="b6633-110">pro Objekt dokumentu, pro který jsou definovány body sekvence.</span><span class="sxs-lookup"><span data-stu-id="b6633-110">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="b6633-111">pro `ULONG32`Který označuje velikost jednotlivých `offsets` `lines` `columns` `endLines` `endColumns` vyrovnávacích pamětí,,, a.</span><span class="sxs-lookup"><span data-stu-id="b6633-111">[in] A `ULONG32` that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="b6633-112">pro Posun bodů sekvence měřený od začátku metody</span><span class="sxs-lookup"><span data-stu-id="b6633-112">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="b6633-113">pro Počáteční čísla řádků bodů sekvence.</span><span class="sxs-lookup"><span data-stu-id="b6633-113">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="b6633-114">pro Čísla počátečních sloupců bodů sekvence</span><span class="sxs-lookup"><span data-stu-id="b6633-114">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="b6633-115">pro Koncová čísla řádků bodů sekvence.</span><span class="sxs-lookup"><span data-stu-id="b6633-115">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="b6633-116">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="b6633-116">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="b6633-117">pro Čísla koncových sloupců bodů sekvence.</span><span class="sxs-lookup"><span data-stu-id="b6633-117">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="b6633-118">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="b6633-118">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6633-119">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b6633-119">Return Value</span></span>  
 <span data-ttu-id="b6633-120">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="b6633-120">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6633-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b6633-121">Requirements</span></span>  
 <span data-ttu-id="b6633-122">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b6633-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6633-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6633-123">See also</span></span>

- [<span data-ttu-id="b6633-124">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6633-124">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
