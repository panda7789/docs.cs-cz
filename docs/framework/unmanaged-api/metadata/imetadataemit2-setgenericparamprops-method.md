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
ms.openlocfilehash: 4daf24c1712b18d933da702e9e1ef1cbdbfc3639
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081902"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="f0ee8-102">IMetaDataEmit2::SetGenericParamProps – metoda</span><span class="sxs-lookup"><span data-stu-id="f0ee8-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="f0ee8-103">Nastavuje hodnoty vlastností pro obecný parametr definice odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="f0ee8-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0ee8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0ee8-104">Syntax</span></span>  
  
```  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,   
    [in] DWORD            dwParamFlags,   
    [in] LPCWSTR          szName,   
    [in] DWORD            reserved,   
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0ee8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0ee8-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="f0ee8-106">[in] Token pro definice obecných parametrů, pro kterou chcete nastavit hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f0ee8-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="f0ee8-107">[in] Hodnota [corgenericparamattr –](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) výčet, který popisuje typu pro obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="f0ee8-107">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="f0ee8-108">[in] Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0ee8-108">[in] Optional.</span></span> <span data-ttu-id="f0ee8-109">Název parametru, pro kterou chcete nastavit hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f0ee8-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="f0ee8-110">[in] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="f0ee8-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="f0ee8-111">[in] Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f0ee8-111">[in] Optional.</span></span> <span data-ttu-id="f0ee8-112">Ukončit nulou pole omezení typu.</span><span class="sxs-lookup"><span data-stu-id="f0ee8-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="f0ee8-113">Členy pole musí být `mdTypeDef`, `mdTypeRef`, nebo `mdTypeSpec` token metadat.</span><span class="sxs-lookup"><span data-stu-id="f0ee8-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0ee8-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f0ee8-114">Requirements</span></span>  
 <span data-ttu-id="f0ee8-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0ee8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0ee8-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f0ee8-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f0ee8-117">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f0ee8-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="f0ee8-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f0ee8-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f0ee8-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0ee8-119">See also</span></span>

- [<span data-ttu-id="f0ee8-120">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f0ee8-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="f0ee8-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f0ee8-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
