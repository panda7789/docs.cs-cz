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
ms.openlocfilehash: 5fc71bf240b89afadbf8f2ba10906322921bdda2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175327"
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="24b26-102">IMetaDataImport::GetPropertyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="24b26-102">IMetaDataImport::GetPropertyProps Method</span></span>
<span data-ttu-id="24b26-103">Získá metadata pro vlastnost reprezentované zadaný token.</span><span class="sxs-lookup"><span data-stu-id="24b26-103">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24b26-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24b26-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="24b26-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="24b26-105">Parameters</span></span>  
 `prop`  
 <span data-ttu-id="24b26-106">[v] Token, který představuje vlastnost vrátit metadata.</span><span class="sxs-lookup"><span data-stu-id="24b26-106">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="24b26-107">[out] Ukazatel na TypeDef token, který představuje typ, který implementuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="24b26-107">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="24b26-108">[out] Vyrovnávací paměť pro uložení názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="24b26-108">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="24b26-109">[v] Velikost v široké `szProperty`znaky .</span><span class="sxs-lookup"><span data-stu-id="24b26-109">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="24b26-110">[out] Počet širokých znaků `szProperty`vrácených v .</span><span class="sxs-lookup"><span data-stu-id="24b26-110">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="24b26-111">[out] Ukazatel na všechny příznaky atributů aplikované na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="24b26-111">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="24b26-112">Tato hodnota je bitová maska z [corpropertyattr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="24b26-112">This value is a bitmask from the [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="24b26-113">[out] Ukazatel na podpis metadat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="24b26-113">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="24b26-114">[out] Počet vrácených bajtů `ppvSig`v .</span><span class="sxs-lookup"><span data-stu-id="24b26-114">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="24b26-115">[out] Příznak určující typ konstanty, která je výchozí hodnotou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="24b26-115">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="24b26-116">Tato hodnota je z CorElementType výčtu.</span><span class="sxs-lookup"><span data-stu-id="24b26-116">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="24b26-117">[out] Ukazatel na bajty, které ukládají výchozí hodnotu pro tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="24b26-117">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="24b26-118">[out] Velikost v širokých `ppDefaultValue`znaků `pdwCPlusTypeFlag` , pokud je ELEMENT_TYPE_STRING; v opačném případě tato hodnota není relevantní.</span><span class="sxs-lookup"><span data-stu-id="24b26-118">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="24b26-119">V takovém případě `ppDefaultValue` je délka odvodit z typu, který je určen `pdwCPlusTypeFlag`.</span><span class="sxs-lookup"><span data-stu-id="24b26-119">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="24b26-120">[out] Ukazatel na token MethodDef, který představuje metodu přístupového objektu set pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="24b26-120">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="24b26-121">[out] Ukazatel na Token MethodDef, který představuje metodu get accessor pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="24b26-121">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="24b26-122">[out] Pole Tokeny MethodDef, které představují jiné metody přidružené k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="24b26-122">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="24b26-123">[v] Maximální velikost `rmdOtherMethod` pole.</span><span class="sxs-lookup"><span data-stu-id="24b26-123">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="24b26-124">Pokud neposkytnete pole dostatečně velké pro všechny metody, jsou přeskočeny bez upozornění.</span><span class="sxs-lookup"><span data-stu-id="24b26-124">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="24b26-125">[out] Počet tokenů MethodDef vrácených v `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="24b26-125">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24b26-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="24b26-126">Requirements</span></span>  
 <span data-ttu-id="24b26-127">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24b26-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24b26-128">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="24b26-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="24b26-129">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="24b26-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="24b26-130">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24b26-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24b26-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="24b26-131">See also</span></span>

- [<span data-ttu-id="24b26-132">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="24b26-132">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="24b26-133">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="24b26-133">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
