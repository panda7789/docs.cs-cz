---
title: IMetaDataImport::GetPropertyProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 81680825daff2cd2358da7b3956782020edf4791
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672055"
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="f978f-102">IMetaDataImport::GetPropertyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="f978f-102">IMetaDataImport::GetPropertyProps Method</span></span>
<span data-ttu-id="f978f-103">Získá metadata pro vlastnost reprezentována zadaného tokenu.</span><span class="sxs-lookup"><span data-stu-id="f978f-103">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f978f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f978f-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="f978f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f978f-105">Parameters</span></span>  
 `prop`  
 <span data-ttu-id="f978f-106">[in] Token, který představuje vrátit metadata pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f978f-106">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="f978f-107">[out] Ukazatel, který představuje typ, který implementuje vlastnost token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="f978f-107">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="f978f-108">[out] Vyrovnávací paměť pro název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f978f-108">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="f978f-109">[in] Velikost v širokých znaků `szProperty`.</span><span class="sxs-lookup"><span data-stu-id="f978f-109">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="f978f-110">[out] Počet širokých znaků, které jsou vráceny v `szProperty`.</span><span class="sxs-lookup"><span data-stu-id="f978f-110">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="f978f-111">[out] Ukazatel na libovolný atribut příznaky použité na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f978f-111">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="f978f-112">Tato hodnota je bitová maska z [corpropertyattr –](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="f978f-112">This value is a bitmask from the [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="f978f-113">[out] Ukazatel na podpis metadat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f978f-113">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="f978f-114">[out] Počet bajtů vrácených v `ppvSig`.</span><span class="sxs-lookup"><span data-stu-id="f978f-114">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="f978f-115">[out] Příznak, který určuje typ konstanty, která je výchozí hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f978f-115">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="f978f-116">Tato hodnota je z corelementtype – výčet.</span><span class="sxs-lookup"><span data-stu-id="f978f-116">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="f978f-117">[out] Ukazatel na počet bajtů, které ukládají výchozí hodnota této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f978f-117">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="f978f-118">[out] Velikost v širokých znaků `ppDefaultValue`, pokud `pdwCPlusTypeFlag` je ELEMENT_TYPE_STRING; v opačném případě tato hodnota není relevantní.</span><span class="sxs-lookup"><span data-stu-id="f978f-118">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="f978f-119">V takovém případě délka `ppDefaultValue` je odvozen od typu určeného `pdwCPlusTypeFlag`.</span><span class="sxs-lookup"><span data-stu-id="f978f-119">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="f978f-120">[out] Ukazatel na token MethodDef, který představuje metody přístupového objektu set pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f978f-120">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="f978f-121">[out] Ukazatel na token MethodDef, který představuje metodu přístupového objektu get pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f978f-121">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="f978f-122">[out] Pole MethodDef tokeny, které představují další metody asociované s vlastností.</span><span class="sxs-lookup"><span data-stu-id="f978f-122">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f978f-123">[in] Maximální velikost `rmdOtherMethod` pole.</span><span class="sxs-lookup"><span data-stu-id="f978f-123">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="f978f-124">Pokud nezadáte pole dostatečně velký pro všechny metody, přeskočí se bez upozornění.</span><span class="sxs-lookup"><span data-stu-id="f978f-124">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="f978f-125">[out] Počet tokenů MethodDef vrácené v `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="f978f-125">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f978f-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f978f-126">Requirements</span></span>  
 <span data-ttu-id="f978f-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f978f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f978f-128">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f978f-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f978f-129">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f978f-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f978f-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f978f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f978f-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f978f-131">See also</span></span>
- [<span data-ttu-id="f978f-132">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f978f-132">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f978f-133">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f978f-133">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
