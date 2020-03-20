---
title: IMetaDataEmit2::SetGenericParamProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type:
- apiref
ms.openlocfilehash: fd7f149e806727d849cdceb3ffbc5dc7392fcf1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177413"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="e88be-102">IMetaDataEmit2::SetGenericParamProps – metoda</span><span class="sxs-lookup"><span data-stu-id="e88be-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="e88be-103">Nastaví hodnoty vlastností pro definici obecného parametru, na kterou odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="e88be-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e88be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e88be-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,
    [in] DWORD            dwParamFlags,
    [in] LPCWSTR          szName,
    [in] DWORD            reserved,
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e88be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e88be-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="e88be-106">[v] Token pro definici obecného parametru, pro který chcete nastavit hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e88be-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="e88be-107">[v] Hodnota [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) výčtu, který popisuje typ pro obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="e88be-107">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="e88be-108">[v] Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e88be-108">[in] Optional.</span></span> <span data-ttu-id="e88be-109">Název parametru, pro který chcete nastavit hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e88be-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="e88be-110">[v] Vyhrazeno pro budoucí rozšiřitelnost.</span><span class="sxs-lookup"><span data-stu-id="e88be-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="e88be-111">[v] Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e88be-111">[in] Optional.</span></span> <span data-ttu-id="e88be-112">Pole typu s nulovým ukončem.</span><span class="sxs-lookup"><span data-stu-id="e88be-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="e88be-113">Členové pole musí `mdTypeDef` `mdTypeRef`být `mdTypeSpec` token , nebo metadat.</span><span class="sxs-lookup"><span data-stu-id="e88be-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e88be-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e88be-114">Requirements</span></span>  
 <span data-ttu-id="e88be-115">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e88be-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e88be-116">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="e88be-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e88be-117">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e88be-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e88be-118">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e88be-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e88be-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="e88be-119">See also</span></span>

- [<span data-ttu-id="e88be-120">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e88be-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="e88be-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e88be-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
