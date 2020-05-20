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
ms.openlocfilehash: 451cfecde7e14fad9d3fed3367112e1fb59796e5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615141"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="b9d4c-102">ISymUnmanagedMethod::GetSequencePoints – metoda</span><span class="sxs-lookup"><span data-stu-id="b9d4c-102">ISymUnmanagedMethod::GetSequencePoints Method</span></span>
<span data-ttu-id="b9d4c-103">Načte všechny body sekvence v rámci této metody.</span><span class="sxs-lookup"><span data-stu-id="b9d4c-103">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9d4c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9d4c-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b9d4c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b9d4c-105">Parameters</span></span>  
 `cPoints`  
 <span data-ttu-id="b9d4c-106">pro A `ULONG32` který přijímá velikost `offsets` `documents` polí,, `lines` , `columns` , `endLines` a `endColumns` .</span><span class="sxs-lookup"><span data-stu-id="b9d4c-106">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="b9d4c-107">mimo Ukazatel na `ULONG32` , který přijímá délku vyrovnávací paměti vyžadované k umístění bodů sekvence.</span><span class="sxs-lookup"><span data-stu-id="b9d4c-107">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="b9d4c-108">pro Pole, do kterého se má uložit posun jazyka MSIL (Microsoft Intermediate Language) od začátku metody pro body sekvence.</span><span class="sxs-lookup"><span data-stu-id="b9d4c-108">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="b9d4c-109">pro Pole, do kterého se mají ukládat dokumenty, ve kterých jsou umístěny body sekvence.</span><span class="sxs-lookup"><span data-stu-id="b9d4c-109">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="b9d4c-110">pro Pole, do kterého se mají ukládat řádky v dokumentech, ve kterých jsou umístěny body sekvence.</span><span class="sxs-lookup"><span data-stu-id="b9d4c-110">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="b9d4c-111">pro Pole, do kterého se mají ukládat sloupce v dokumentech, ve kterých jsou umístěny body sekvence.</span><span class="sxs-lookup"><span data-stu-id="b9d4c-111">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="b9d4c-112">pro Pole řádků v dokumentech, na kterých končí body sekvence</span><span class="sxs-lookup"><span data-stu-id="b9d4c-112">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="b9d4c-113">pro Pole sloupců v dokumentech, na kterých končí body sekvence</span><span class="sxs-lookup"><span data-stu-id="b9d4c-113">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9d4c-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b9d4c-114">Return Value</span></span>  
 <span data-ttu-id="b9d4c-115">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="b9d4c-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9d4c-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9d4c-116">Requirements</span></span>  
 <span data-ttu-id="b9d4c-117">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b9d4c-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9d4c-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9d4c-118">See also</span></span>

- [<span data-ttu-id="b9d4c-119">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9d4c-119">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
