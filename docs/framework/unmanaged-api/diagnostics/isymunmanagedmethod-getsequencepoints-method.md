---
title: ISymUnmanagedMethod::GetSequencePoints – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d8cfde8f0eb14919c12d261c3f9f7209365829c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759457"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="c0689-102">ISymUnmanagedMethod::GetSequencePoints – metoda</span><span class="sxs-lookup"><span data-stu-id="c0689-102">ISymUnmanagedMethod::GetSequencePoints Method</span></span>
<span data-ttu-id="c0689-103">Získá všechny body sekvence v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="c0689-103">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0689-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0689-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0689-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c0689-105">Parameters</span></span>  
 `cPoints`  
 <span data-ttu-id="c0689-106">[in] A `ULONG32` , která obdrží velikost `offsets`, `documents`, `lines`, `columns`, `endLines`, a `endColumns` pole.</span><span class="sxs-lookup"><span data-stu-id="c0689-106">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="c0689-107">[out] Ukazatel `ULONG32` , která obdrží délka vyrovnávací paměti musí obsahovat body sekvence.</span><span class="sxs-lookup"><span data-stu-id="c0689-107">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="c0689-108">[in] Pole pro uložení Microsoft intermediate language (MSIL) posun od začátku metody pro body sekvence.</span><span class="sxs-lookup"><span data-stu-id="c0689-108">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="c0689-109">[in] Pole ve kterých se mají ukládat dokumenty, ve kterých jsou umístěny body sekvence.</span><span class="sxs-lookup"><span data-stu-id="c0689-109">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="c0689-110">[in] Pole pro uložení řádky v dokumentech, na kterých jsou umístěny body sekvence.</span><span class="sxs-lookup"><span data-stu-id="c0689-110">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="c0689-111">[in] Pole pro uložení sloupce v dokumentech, na kterých jsou umístěny body sekvence.</span><span class="sxs-lookup"><span data-stu-id="c0689-111">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="c0689-112">[in] Pole řádků v dokumentech, na které odkazuje sekvence end.</span><span class="sxs-lookup"><span data-stu-id="c0689-112">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="c0689-113">[in] Pole sloupců v dokumentech, na které odkazuje sekvence end.</span><span class="sxs-lookup"><span data-stu-id="c0689-113">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0689-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c0689-114">Return Value</span></span>  
 <span data-ttu-id="c0689-115">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="c0689-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0689-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c0689-116">Requirements</span></span>  
 <span data-ttu-id="c0689-117">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c0689-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0689-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0689-118">See also</span></span>

- [<span data-ttu-id="c0689-119">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0689-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
