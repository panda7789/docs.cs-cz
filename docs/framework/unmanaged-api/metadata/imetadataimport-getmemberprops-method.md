---
title: IMetaDataImport::GetMemberProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
ms.openlocfilehash: 72e14ea0414ebdeb8f54a4bdef8ce5208fc8ef72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177233"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="ac6e7-102">IMetaDataImport::GetMemberProps – metoda</span><span class="sxs-lookup"><span data-stu-id="ac6e7-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="ac6e7-103">Získá informace uložené v metadatech pro definici zadaného člena, včetně názvu, <xref:System.Type> binárního podpisu a relativní virtuální adresy člena, na který odkazuje zadaný token metadat.</span><span class="sxs-lookup"><span data-stu-id="ac6e7-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="ac6e7-104">Toto je jednoduchá pomocná metoda: pokud *mb* je MethodDef, pak **GetMethodProps** je volána; Pokud *mb* je FieldDef, pak **GetFieldProps** je volána.</span><span class="sxs-lookup"><span data-stu-id="ac6e7-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="ac6e7-105">Podrobnosti naleznete v následujících dalších metodách.</span><span class="sxs-lookup"><span data-stu-id="ac6e7-105">See these other methods for details.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="ac6e7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac6e7-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,
   [in]  ULONG             cchMember,
   [out] ULONG             *pchMember,
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] ULONG             *pulCodeRVA,
   [out] DWORD             *pdwImplFlags,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac6e7-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac6e7-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="ac6e7-108">[v] Token, který odkazuje na člena získat přidružená metadata.</span><span class="sxs-lookup"><span data-stu-id="ac6e7-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="ac6e7-109">[out] Ukazatel na token metadat, který představuje třídu člena.</span><span class="sxs-lookup"><span data-stu-id="ac6e7-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="ac6e7-110">[out] Jméno člena.</span><span class="sxs-lookup"><span data-stu-id="ac6e7-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="ac6e7-111">[v] Velikost v široké znaky `szMember` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ac6e7-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="ac6e7-112">[out] Velikost širokých znaků vráceného názvu.</span><span class="sxs-lookup"><span data-stu-id="ac6e7-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="ac6e7-113">[out] Všechny hodnoty příznaku použité na člena.</span><span class="sxs-lookup"><span data-stu-id="ac6e7-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="ac6e7-114">[out] Ukazatel na podpis binárních metadat člena.</span><span class="sxs-lookup"><span data-stu-id="ac6e7-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="ac6e7-115">[out] Velikost v bajtů `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="ac6e7-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="ac6e7-116">[out] Ukazatel na relativní virtuální adresu člena.</span><span class="sxs-lookup"><span data-stu-id="ac6e7-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="ac6e7-117">[out] Všechny příznaky implementace metody přidružené k členu.</span><span class="sxs-lookup"><span data-stu-id="ac6e7-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="ac6e7-118">[out] Příznak, který <xref:System.ValueType>označuje .</span><span class="sxs-lookup"><span data-stu-id="ac6e7-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="ac6e7-119">Je to jedna `ELEMENT_TYPE_*` z hodnot.</span><span class="sxs-lookup"><span data-stu-id="ac6e7-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="ac6e7-120">[out] Konstantní hodnota řetězce vrácená tímto členem.</span><span class="sxs-lookup"><span data-stu-id="ac6e7-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="ac6e7-121">[out] Velikost ve znacích `ppValue`, `ppValue` nebo nula, pokud není obsahovat řetězec.</span><span class="sxs-lookup"><span data-stu-id="ac6e7-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac6e7-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ac6e7-122">Requirements</span></span>  
 <span data-ttu-id="ac6e7-123">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac6e7-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac6e7-124">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="ac6e7-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ac6e7-125">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ac6e7-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ac6e7-126">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac6e7-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac6e7-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac6e7-127">See also</span></span>

- [<span data-ttu-id="ac6e7-128">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ac6e7-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ac6e7-129">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ac6e7-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
