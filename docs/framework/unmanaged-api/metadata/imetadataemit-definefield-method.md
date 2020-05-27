---
title: IMetaDataEmit::DefineField – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
ms.openlocfilehash: ccc4843864f375c167acdb12575c282dbe3a49e1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004813"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="7339c-102">IMetaDataEmit::DefineField – metoda</span><span class="sxs-lookup"><span data-stu-id="7339c-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="7339c-103">Vytvoří definici pro pole se zadaným podpisem metadat a získá token do této definice pole.</span><span class="sxs-lookup"><span data-stu-id="7339c-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7339c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7339c-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineField (
    [in]  mdTypeDef   td,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwFieldFlags,
    [in]  PCCOR_SIGNATURE pvSigBlob,
    [in]  ULONG       cbSigBlob,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue,
    [out] mdFieldDef  *pmd
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7339c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7339c-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="7339c-106">pro `mdTypeDef`Token pro ohraničující třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7339c-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="7339c-107">pro Název pole v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="7339c-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="7339c-108">pro Atributy pole</span><span class="sxs-lookup"><span data-stu-id="7339c-108">[in] The field attributes.</span></span> <span data-ttu-id="7339c-109">Toto je Bitová maska `CorFieldAttr` hodnot.</span><span class="sxs-lookup"><span data-stu-id="7339c-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="7339c-110">pro Podpis pole jako objekt BLOB</span><span class="sxs-lookup"><span data-stu-id="7339c-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="7339c-111">pro Počet bajtů v `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="7339c-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="7339c-112">pro `ELEMENT_TYPE_` *\** Pro hodnotu konstanty.</span><span class="sxs-lookup"><span data-stu-id="7339c-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="7339c-113">Toto je `CorElementType` hodnota.</span><span class="sxs-lookup"><span data-stu-id="7339c-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="7339c-114">Pokud nedefinujete konstantní hodnotu pro pole, použijte `ELEMENT_TYPE_END` .</span><span class="sxs-lookup"><span data-stu-id="7339c-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="7339c-115">pro Hodnota konstanty pro pole</span><span class="sxs-lookup"><span data-stu-id="7339c-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="7339c-116">pro Velikost v (Unicode) znaků `pValue` .</span><span class="sxs-lookup"><span data-stu-id="7339c-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="7339c-117">mimo `mdFieldDef`Přiřazený token.</span><span class="sxs-lookup"><span data-stu-id="7339c-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7339c-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7339c-118">Requirements</span></span>  
 <span data-ttu-id="7339c-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7339c-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7339c-120">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7339c-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7339c-121">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="7339c-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7339c-122">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7339c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7339c-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="7339c-123">See also</span></span>

- [<span data-ttu-id="7339c-124">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7339c-124">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="7339c-125">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7339c-125">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
