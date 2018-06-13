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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2d74ee7512f640ab906f1119f61e4998b5e882eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445684"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="b3881-102">IMetaDataEmit2::SetGenericParamProps – metoda</span><span class="sxs-lookup"><span data-stu-id="b3881-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="b3881-103">Nastaví hodnoty vlastností pro definici obecný parametr odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="b3881-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3881-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3881-104">Syntax</span></span>  
  
```  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,   
    [in] DWORD            dwParamFlags,   
    [in] LPCWSTR          szName,   
    [in] DWORD            reserved,   
    [in] mdToken          rtkConstraints[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3881-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3881-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="b3881-106">[v] Token pro danou definici obecný parametr, pro kterou chcete nastavit hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b3881-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="b3881-107">[v] Hodnota [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) výčet, který popisuje typ pro obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="b3881-107">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="b3881-108">[v] Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="b3881-108">[in] Optional.</span></span> <span data-ttu-id="b3881-109">Název parametru, pro kterou chcete nastavit hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b3881-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="b3881-110">[v] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="b3881-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="b3881-111">[v] Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="b3881-111">[in] Optional.</span></span> <span data-ttu-id="b3881-112">Byl ukončen nula pole Typ omezení.</span><span class="sxs-lookup"><span data-stu-id="b3881-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="b3881-113">Pole členů musí být `mdTypeDef`, `mdTypeRef`, nebo `mdTypeSpec` metadata token.</span><span class="sxs-lookup"><span data-stu-id="b3881-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3881-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b3881-114">Requirements</span></span>  
 <span data-ttu-id="b3881-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3881-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3881-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b3881-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b3881-117">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b3881-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b3881-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3881-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3881-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3881-119">See Also</span></span>  
 [<span data-ttu-id="b3881-120">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3881-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="b3881-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3881-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
