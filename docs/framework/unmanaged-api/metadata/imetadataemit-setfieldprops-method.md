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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f05c6df415a92151783d805799da5bf7dfb6c7a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556100"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="e4ce7-102">IMetaDataEmit::SetFieldProps – metoda</span><span class="sxs-lookup"><span data-stu-id="e4ce7-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="e4ce7-103">Nastaví nebo aktualizuje výchozí hodnota pro pole odkazuje token zadaného pole.</span><span class="sxs-lookup"><span data-stu-id="e4ce7-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4ce7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4ce7-104">Syntax</span></span>  
  
```  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,   
    [in]  DWORD       dwFieldFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4ce7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4ce7-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="e4ce7-106">[in] Token pro cílové pole.</span><span class="sxs-lookup"><span data-stu-id="e4ce7-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="e4ce7-107">[in] Atributy pole.</span><span class="sxs-lookup"><span data-stu-id="e4ce7-107">[in] Field attributes.</span></span> <span data-ttu-id="e4ce7-108">To je bitová maska z `CorFieldAttr` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e4ce7-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="e4ce7-109">[in] `ELEMENT_TYPE_` *\** Pro konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e4ce7-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="e4ce7-110">Jedná se `CorElementType` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e4ce7-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="e4ce7-111">Pokud není definované konstantě, nastavte tuto hodnotu na `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="e4ce7-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="e4ce7-112">[in] Konstantní hodnoty pro pole.</span><span class="sxs-lookup"><span data-stu-id="e4ce7-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="e4ce7-113">[in] Velikost v znaky Unicode z `pValue`.</span><span class="sxs-lookup"><span data-stu-id="e4ce7-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4ce7-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e4ce7-114">Requirements</span></span>  
 <span data-ttu-id="e4ce7-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4ce7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4ce7-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e4ce7-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e4ce7-117">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e4ce7-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4ce7-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4ce7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4ce7-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4ce7-119">See also</span></span>
- [<span data-ttu-id="e4ce7-120">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4ce7-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e4ce7-121">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4ce7-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
