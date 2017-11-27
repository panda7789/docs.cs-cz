---
title: "IMetaDataImport2::EnumMethodSpecs – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.EnumMethodSpecs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: db1968c73d5a1c6e0687bc86f249c70b6c21712c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="78d08-102">IMetaDataImport2::EnumMethodSpecs – metoda</span><span class="sxs-lookup"><span data-stu-id="78d08-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="78d08-103">Získá enumerátor pro pole MethodSpec tokeny přidružený k zadané MethodDef nebo MemberRef token.</span><span class="sxs-lookup"><span data-stu-id="78d08-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78d08-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78d08-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="78d08-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78d08-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="78d08-106">[ve out] Ukazatel na enumerátor pro `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="78d08-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="78d08-107">[v] MemberRef nebo MethodDef tokenu, který představuje metodu, jejichž MethodSpec tokeny mají být ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="78d08-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="78d08-108">Pokud hodnota `tk` je 0 (nula), bude možné provést výčet všech MethodSpec tokenů v oboru.</span><span class="sxs-lookup"><span data-stu-id="78d08-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="78d08-109">[out] Pole MethodSpec tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="78d08-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="78d08-110">[v] Požadovaný maximální počet tokeny umístit `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="78d08-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="78d08-111">[out] Vrácený počet tokeny umístěných v `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="78d08-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78d08-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="78d08-112">Return Value</span></span>  
  
|<span data-ttu-id="78d08-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78d08-113">HRESULT</span></span>|<span data-ttu-id="78d08-114">Popis</span><span class="sxs-lookup"><span data-stu-id="78d08-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="78d08-115">`EnumMethodSpecs`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="78d08-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="78d08-116">`phEnum`nemá žádné elementy člen.</span><span class="sxs-lookup"><span data-stu-id="78d08-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="78d08-117">V takovém případě `pcMethodSpecs` je nastaven na hodnotu 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="78d08-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="78d08-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78d08-118">Requirements</span></span>  
 <span data-ttu-id="78d08-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78d08-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78d08-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="78d08-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="78d08-121">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78d08-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="78d08-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78d08-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78d08-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="78d08-123">See Also</span></span>  
 [<span data-ttu-id="78d08-124">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78d08-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="78d08-125">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78d08-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
