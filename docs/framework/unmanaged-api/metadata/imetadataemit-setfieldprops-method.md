---
title: IMetaDataEmit::SetFieldProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type:
- apiref
ms.openlocfilehash: b921118f7c43edef3c07cbb34cbbd9119d36ce51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177554"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="51837-102">IMetaDataEmit::SetFieldProps – metoda</span><span class="sxs-lookup"><span data-stu-id="51837-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="51837-103">Nastaví nebo aktualizuje výchozí hodnotu pro pole odkazované zadaným tokenem pole.</span><span class="sxs-lookup"><span data-stu-id="51837-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51837-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51837-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51837-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51837-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="51837-106">[v] Token pro cílové pole.</span><span class="sxs-lookup"><span data-stu-id="51837-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="51837-107">[v] Atributy pole.</span><span class="sxs-lookup"><span data-stu-id="51837-107">[in] Field attributes.</span></span> <span data-ttu-id="51837-108">Toto je bitová maska `CorFieldAttr` hodnot.</span><span class="sxs-lookup"><span data-stu-id="51837-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="51837-109">[v] Pro `ELEMENT_TYPE_` *\** konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="51837-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="51837-110">To je `CorElementType` hodnota.</span><span class="sxs-lookup"><span data-stu-id="51837-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="51837-111">Pokud konstanta není definována, nastavte `ELEMENT_TYPE_END`tuto hodnotu na .</span><span class="sxs-lookup"><span data-stu-id="51837-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="51837-112">[v] Konstantní hodnota pole.</span><span class="sxs-lookup"><span data-stu-id="51837-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="51837-113">[v] Velikost znaku Unicode . `pValue`</span><span class="sxs-lookup"><span data-stu-id="51837-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51837-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="51837-114">Requirements</span></span>  
 <span data-ttu-id="51837-115">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51837-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51837-116">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="51837-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="51837-117">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="51837-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51837-118">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51837-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51837-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="51837-119">See also</span></span>

- [<span data-ttu-id="51837-120">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51837-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="51837-121">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51837-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
