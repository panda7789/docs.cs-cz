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
ms.openlocfilehash: c9a35f35d7aea34c0ef08c30415fde75fe71e645
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426047"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="9aa11-102">ISymUnmanagedMethod::GetSequencePoints – metoda</span><span class="sxs-lookup"><span data-stu-id="9aa11-102">ISymUnmanagedMethod::GetSequencePoints Method</span></span>
<span data-ttu-id="9aa11-103">Získá všechny body pořadí v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="9aa11-103">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aa11-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9aa11-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="9aa11-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9aa11-105">Parameters</span></span>  
 `cPoints`  
 <span data-ttu-id="9aa11-106">[v] A `ULONG32` která přijme velikost `offsets`, `documents`, `lines`, `columns`, `endLines`, a `endColumns` pole.</span><span class="sxs-lookup"><span data-stu-id="9aa11-106">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="9aa11-107">[out] Ukazatel na `ULONG32` která přijme délka vyrovnávací paměti musí obsahovat body sekvence.</span><span class="sxs-lookup"><span data-stu-id="9aa11-107">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="9aa11-108">[v] Pole pro uložení zprostředkující Microsoft jazyk MSIL posun od začátku metodu pro body sekvence.</span><span class="sxs-lookup"><span data-stu-id="9aa11-108">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="9aa11-109">[v] Pole, do kterého chcete ukládat dokumenty, ve které se nacházejí body sekvence.</span><span class="sxs-lookup"><span data-stu-id="9aa11-109">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="9aa11-110">[v] Pole pro uložení řádky v dokumentech, na kterých jsou umístěny body sekvence.</span><span class="sxs-lookup"><span data-stu-id="9aa11-110">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="9aa11-111">[v] Pole, do které chcete uložit v dokumentech, na kterých jsou umístěny body pořadí sloupců.</span><span class="sxs-lookup"><span data-stu-id="9aa11-111">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="9aa11-112">[v] Pole řádků v dokumentech, na kterých je pořadí body end.</span><span class="sxs-lookup"><span data-stu-id="9aa11-112">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="9aa11-113">[v] Pole sloupců v dokumentech, na kterých je pořadí body end.</span><span class="sxs-lookup"><span data-stu-id="9aa11-113">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9aa11-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9aa11-114">Return Value</span></span>  
 <span data-ttu-id="9aa11-115">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="9aa11-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9aa11-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9aa11-116">Requirements</span></span>  
 <span data-ttu-id="9aa11-117">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9aa11-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aa11-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="9aa11-118">See Also</span></span>  
 [<span data-ttu-id="9aa11-119">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9aa11-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
