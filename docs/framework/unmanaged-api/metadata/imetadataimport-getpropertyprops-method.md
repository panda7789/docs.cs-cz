---
title: "IMetaDataImport::GetPropertyProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetPropertyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d838f43b500ac3dd0c3b44d9d84dd9fc039c6e16
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="b78a4-102">IMetaDataImport::GetPropertyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="b78a4-102">IMetaDataImport::GetPropertyProps Method</span></span>
<span data-ttu-id="b78a4-103">Získá metadata pro vlastnost reprezentována zadaný token.</span><span class="sxs-lookup"><span data-stu-id="b78a4-103">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b78a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b78a4-104">Syntax</span></span>  
  
```  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,   
   [out] LPCWSTR           szProperty,   
   [in]  ULONG             cchProperty,   
   [out] ULONG             *pchProperty,   
   [out] DWORD             *pdwPropFlags,   
   [out] PCCOR_SIGNATURE   *ppvSig,   
   [out] ULONG             *pbSig,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,   
   [out] mdMethodDef       *pmdGetter,   
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,   
   [out] ULONG             *pcOtherMethod   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b78a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b78a4-105">Parameters</span></span>  
 `prop`  
 <span data-ttu-id="b78a4-106">[v] Token, který reprezentuje vlastnost vrátit metadata pro.</span><span class="sxs-lookup"><span data-stu-id="b78a4-106">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="b78a4-107">[out] Ukazatel na TypeDef token, který představuje typ, který implementuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b78a4-107">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="b78a4-108">[out] Vyrovnávací paměť pro název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b78a4-108">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="b78a4-109">[v] Velikost v široké znaky `szProperty`.</span><span class="sxs-lookup"><span data-stu-id="b78a4-109">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="b78a4-110">[out] Počet široké znaky, vrátí se v `szProperty`.</span><span class="sxs-lookup"><span data-stu-id="b78a4-110">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="b78a4-111">[out] Ukazatel na žádné příznaky atribut použit na vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b78a4-111">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="b78a4-112">Tato hodnota je bitová maska z [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="b78a4-112">This value is a bitmask from the [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="b78a4-113">[out] Ukazatel na podpis metadata vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b78a4-113">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="b78a4-114">[out] Počet bajtů vrácených v `ppvSig`.</span><span class="sxs-lookup"><span data-stu-id="b78a4-114">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="b78a4-115">[out] Příznak určující typ konstanta, která je výchozí hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b78a4-115">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="b78a4-116">Tato hodnota je z CorElementType – výčet.</span><span class="sxs-lookup"><span data-stu-id="b78a4-116">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="b78a4-117">[out] Ukazatel na počet bajtů, které ukládají výchozí hodnotu pro tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b78a4-117">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="b78a4-118">[out] Velikost v široké znaky `ppDefaultValue`, pokud `pdwCPlusTypeFlag` je ELEMENT_TYPE_STRING; jinak, tato hodnota není relevantní.</span><span class="sxs-lookup"><span data-stu-id="b78a4-118">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="b78a4-119">V takovém případě délka `ppDefaultValue` je odvozen od typu, která je zadána `pdwCPlusTypeFlag`.</span><span class="sxs-lookup"><span data-stu-id="b78a4-119">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="b78a4-120">[out] Ukazatel na MethodDef token, který představuje metodu přistupující objekt set pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b78a4-120">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="b78a4-121">[out] Ukazatel na MethodDef token, který představuje metodu get přistupujícího objektu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b78a4-121">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="b78a4-122">[out] Pole MethodDef tokeny, které představují další metody související s vlastností.</span><span class="sxs-lookup"><span data-stu-id="b78a4-122">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b78a4-123">[v] Maximální velikost `rmdOtherMethod` pole.</span><span class="sxs-lookup"><span data-stu-id="b78a4-123">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="b78a4-124">Pokud nezadáte pole dostatečně velký pro uložení všech metod, jsou přeskočena bez upozornění.</span><span class="sxs-lookup"><span data-stu-id="b78a4-124">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="b78a4-125">[out] Počet MethodDef tokeny, vrátí se v `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="b78a4-125">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b78a4-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b78a4-126">Requirements</span></span>  
 <span data-ttu-id="b78a4-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b78a4-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b78a4-128">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b78a4-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b78a4-129">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b78a4-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b78a4-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b78a4-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b78a4-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="b78a4-131">See Also</span></span>  
 [<span data-ttu-id="b78a4-132">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b78a4-132">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b78a4-133">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b78a4-133">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
