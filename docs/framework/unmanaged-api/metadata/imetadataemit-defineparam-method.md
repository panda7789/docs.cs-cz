---
title: IMetaDataEmit::DefineParam – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
ms.openlocfilehash: a58e03875ec021b41479085fa9e27a4321ae965e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004345"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="962f8-102">IMetaDataEmit::DefineParam – metoda</span><span class="sxs-lookup"><span data-stu-id="962f8-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="962f8-103">Vytvoří definici parametru se specifikovanou signaturou pro metodu, na kterou se odkazuje pomocí zadaného tokenu, a získá token pro tuto definici parametru.</span><span class="sxs-lookup"><span data-stu-id="962f8-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="962f8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="962f8-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineParam (  
    [in]  mdMethodDef md,
    [in]  ULONG       ulParamSeq,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,
    [out] mdParamDef  *ppd
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="962f8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="962f8-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="962f8-106">pro Token pro metodu, jejíž parametr je právě definován.</span><span class="sxs-lookup"><span data-stu-id="962f8-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="962f8-107">pro Pořadové číslo parametru.</span><span class="sxs-lookup"><span data-stu-id="962f8-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="962f8-108">pro Název parametru v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="962f8-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="962f8-109">pro Příznaky pro parametr</span><span class="sxs-lookup"><span data-stu-id="962f8-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="962f8-110">Toto je Bitová maska `CorParamAttr` hodnot.</span><span class="sxs-lookup"><span data-stu-id="962f8-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="962f8-111">[in] `ELEMENT_TYPE_` *\** pro hodnotu konstanty.</span><span class="sxs-lookup"><span data-stu-id="962f8-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="962f8-112">pro Hodnota konstanty pro parametr</span><span class="sxs-lookup"><span data-stu-id="962f8-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="962f8-113">pro Velikost (v Unicode znacích) `pValue` .</span><span class="sxs-lookup"><span data-stu-id="962f8-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="962f8-114">mimo `mdParamDef`Přiřazený token.</span><span class="sxs-lookup"><span data-stu-id="962f8-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="962f8-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="962f8-115">Remarks</span></span>  
 <span data-ttu-id="962f8-116">Hodnoty sekvence začínají na `ulParamSeq` 1 pro parametry.</span><span class="sxs-lookup"><span data-stu-id="962f8-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="962f8-117">Návratová hodnota má pořadové číslo 0.</span><span class="sxs-lookup"><span data-stu-id="962f8-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="962f8-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="962f8-118">Requirements</span></span>  
 <span data-ttu-id="962f8-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="962f8-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="962f8-120">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="962f8-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="962f8-121">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="962f8-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="962f8-122">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="962f8-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="962f8-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="962f8-123">See also</span></span>

- [<span data-ttu-id="962f8-124">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="962f8-124">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="962f8-125">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="962f8-125">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
