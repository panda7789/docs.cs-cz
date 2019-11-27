---
title: IMetaDataImport2::GetGenericParamProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
ms.openlocfilehash: a8c5dd263401002deaee3d21f1e41b41a29faec2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427293"
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="b1c7d-102">IMetaDataImport2::GetGenericParamProps – metoda</span><span class="sxs-lookup"><span data-stu-id="b1c7d-102">IMetaDataImport2::GetGenericParamProps Method</span></span>
<span data-ttu-id="b1c7d-103">Získá metadata přidružená k obecnému parametru reprezentovanému zadaným tokenem.</span><span class="sxs-lookup"><span data-stu-id="b1c7d-103">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1c7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1c7d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1c7d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1c7d-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="b1c7d-106">pro Token, který představuje obecný parametr, pro který se mají vracet metadata</span><span class="sxs-lookup"><span data-stu-id="b1c7d-106">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="b1c7d-107">mimo Pořadové místo parametru `Type` v nadřazeném konstruktoru nebo metodě.</span><span class="sxs-lookup"><span data-stu-id="b1c7d-107">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="b1c7d-108">mimo Hodnota výčtu [CorGenericParamAttr –](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) , která popisuje `Type` pro obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="b1c7d-108">[out] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="b1c7d-109">mimo Token TypeDef nebo MethodDef, který představuje vlastníka parametru.</span><span class="sxs-lookup"><span data-stu-id="b1c7d-109">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="b1c7d-110">mimo Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="b1c7d-110">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="b1c7d-111">mimo Název obecného parametru.</span><span class="sxs-lookup"><span data-stu-id="b1c7d-111">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b1c7d-112">pro Velikost vyrovnávací paměti `wzName`.</span><span class="sxs-lookup"><span data-stu-id="b1c7d-112">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="b1c7d-113">mimo Vrácená velikost názvu, v rámci velkých znaků.</span><span class="sxs-lookup"><span data-stu-id="b1c7d-113">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1c7d-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1c7d-114">Requirements</span></span>  
 <span data-ttu-id="b1c7d-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1c7d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1c7d-116">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b1c7d-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1c7d-117">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="b1c7d-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b1c7d-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1c7d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1c7d-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1c7d-119">See also</span></span>

- [<span data-ttu-id="b1c7d-120">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b1c7d-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="b1c7d-121">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b1c7d-121">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
