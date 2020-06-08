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
ms.openlocfilehash: 8feba8e67f3a90dd48fd957065a9c166c204b87c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492730"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="71b58-102">IMetaDataEmit2::SetGenericParamProps – metoda</span><span class="sxs-lookup"><span data-stu-id="71b58-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="71b58-103">Nastaví hodnoty vlastností pro definici obecného parametru, na kterou odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="71b58-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71b58-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71b58-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,
    [in] DWORD            dwParamFlags,
    [in] LPCWSTR          szName,
    [in] DWORD            reserved,
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71b58-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="71b58-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="71b58-106">pro Token pro definici obecného parametru, pro který chcete nastavit hodnoty.</span><span class="sxs-lookup"><span data-stu-id="71b58-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="71b58-107">pro Hodnota výčtu [CorGenericParamAttr –](corgenericparamattr-enumeration.md) , která popisuje typ obecného parametru.</span><span class="sxs-lookup"><span data-stu-id="71b58-107">[in] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="71b58-108">pro Volitelné.</span><span class="sxs-lookup"><span data-stu-id="71b58-108">[in] Optional.</span></span> <span data-ttu-id="71b58-109">Název parametru, pro který chcete nastavit hodnoty.</span><span class="sxs-lookup"><span data-stu-id="71b58-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="71b58-110">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="71b58-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="71b58-111">pro Volitelné.</span><span class="sxs-lookup"><span data-stu-id="71b58-111">[in] Optional.</span></span> <span data-ttu-id="71b58-112">Pole s nulovým zakončením v poli omezení typu.</span><span class="sxs-lookup"><span data-stu-id="71b58-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="71b58-113">Členy pole musí být `mdTypeDef` `mdTypeRef` token metadat, nebo `mdTypeSpec` .</span><span class="sxs-lookup"><span data-stu-id="71b58-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71b58-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="71b58-114">Requirements</span></span>  
 <span data-ttu-id="71b58-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71b58-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71b58-116">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="71b58-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="71b58-117">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="71b58-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="71b58-118">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71b58-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71b58-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71b58-119">See also</span></span>

- [<span data-ttu-id="71b58-120">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="71b58-120">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="71b58-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="71b58-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
