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
ms.openlocfilehash: cac5aaa7ed13b6a48b36ad550da8b73d0deb2ee7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491040"
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="bf8e8-102">IMetaDataImport::GetPropertyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="bf8e8-102">IMetaDataImport::GetPropertyProps Method</span></span>
<span data-ttu-id="bf8e8-103">Získá metadata pro vlastnost představovanou zadaným tokenem.</span><span class="sxs-lookup"><span data-stu-id="bf8e8-103">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf8e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf8e8-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="bf8e8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf8e8-105">Parameters</span></span>  
 `prop`  
 <span data-ttu-id="bf8e8-106">pro Token, který představuje vlastnost, pro kterou se mají vracet metadata</span><span class="sxs-lookup"><span data-stu-id="bf8e8-106">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="bf8e8-107">mimo Ukazatel na token TypeDef, který představuje typ, který implementuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bf8e8-107">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="bf8e8-108">mimo Vyrovnávací paměť pro uložení názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bf8e8-108">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="bf8e8-109">pro Velikost v různých znacích `szProperty` .</span><span class="sxs-lookup"><span data-stu-id="bf8e8-109">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="bf8e8-110">mimo Počet znaků vrácených v rámci `szProperty` .</span><span class="sxs-lookup"><span data-stu-id="bf8e8-110">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="bf8e8-111">mimo Ukazatel na libovolný příznak atributu aplikovaný na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bf8e8-111">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="bf8e8-112">Tato hodnota je Bitová maska z výčtu [CorPropertyAttr –](corpropertyattr-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="bf8e8-112">This value is a bitmask from the [CorPropertyAttr](corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="bf8e8-113">mimo Ukazatel na podpis metadat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bf8e8-113">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="bf8e8-114">mimo Počet vrácených bajtů `ppvSig` .</span><span class="sxs-lookup"><span data-stu-id="bf8e8-114">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="bf8e8-115">mimo Příznak určující typ konstanty, která je výchozí hodnotou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bf8e8-115">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="bf8e8-116">Tato hodnota pochází z výčtu CorElementType –.</span><span class="sxs-lookup"><span data-stu-id="bf8e8-116">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="bf8e8-117">mimo Ukazatel na bajty, které ukládají výchozí hodnotu pro tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bf8e8-117">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="bf8e8-118">mimo Velikost v různých znacích `ppDefaultValue` , pokud `pdwCPlusTypeFlag` je ELEMENT_TYPE_STRING; jinak tato hodnota není relevantní.</span><span class="sxs-lookup"><span data-stu-id="bf8e8-118">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="bf8e8-119">V takovém případě `ppDefaultValue` je délka odvozena od typu, který je určen pomocí `pdwCPlusTypeFlag` .</span><span class="sxs-lookup"><span data-stu-id="bf8e8-119">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="bf8e8-120">mimo Ukazatel na token MethodDef, který představuje metodu set přístupového objektu pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bf8e8-120">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="bf8e8-121">mimo Ukazatel na token MethodDef, který představuje metodu Get přístup k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bf8e8-121">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="bf8e8-122">mimo Pole tokenů MethodDef, které představuje jiné metody přidružené k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bf8e8-122">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bf8e8-123">pro Maximální velikost `rmdOtherMethod` pole.</span><span class="sxs-lookup"><span data-stu-id="bf8e8-123">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="bf8e8-124">Pokud nezadáte pole dostatečně velké pro uložení všech metod, budou vynechána bez upozornění.</span><span class="sxs-lookup"><span data-stu-id="bf8e8-124">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="bf8e8-125">mimo Počet tokenů MethodDef vrácených v `rmdOtherMethod` .</span><span class="sxs-lookup"><span data-stu-id="bf8e8-125">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf8e8-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf8e8-126">Requirements</span></span>  
 <span data-ttu-id="bf8e8-127">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf8e8-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf8e8-128">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bf8e8-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bf8e8-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bf8e8-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bf8e8-130">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf8e8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf8e8-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf8e8-131">See also</span></span>

- [<span data-ttu-id="bf8e8-132">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf8e8-132">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="bf8e8-133">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf8e8-133">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
