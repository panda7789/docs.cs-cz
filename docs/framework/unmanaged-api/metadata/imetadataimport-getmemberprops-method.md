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
ms.openlocfilehash: bc5bbba2fa4a95955e52a2e083a2097178b5d96a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437517"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="fad77-102">IMetaDataImport::GetMemberProps – metoda</span><span class="sxs-lookup"><span data-stu-id="fad77-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="fad77-103">Načte informace uložené v metadatech pro zadanou definici člena, včetně názvu, binárního podpisu a relativní virtuální adresy, <xref:System.Type> člena, na který odkazuje zadaný token metadat.</span><span class="sxs-lookup"><span data-stu-id="fad77-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="fad77-104">Toto je jednoduchá pomocná metoda: Pokud je v *MB* , je zavolána metoda **getmethodprops –** ; Pokud je *MB* FieldDef, pak se zavolá **getfieldprops –** .</span><span class="sxs-lookup"><span data-stu-id="fad77-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="fad77-105">Podrobnosti najdete v těchto dalších metodách.</span><span class="sxs-lookup"><span data-stu-id="fad77-105">See these other methods for details.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="fad77-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fad77-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="fad77-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="fad77-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="fad77-108">pro Token, který odkazuje na člena, aby získal přidružená metadata pro.</span><span class="sxs-lookup"><span data-stu-id="fad77-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="fad77-109">mimo Ukazatel na token metadat, který představuje třídu člena.</span><span class="sxs-lookup"><span data-stu-id="fad77-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="fad77-110">mimo Název člena.</span><span class="sxs-lookup"><span data-stu-id="fad77-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="fad77-111">pro Velikost v rámci velkých písmen `szMember` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="fad77-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="fad77-112">mimo Velikost vráceného názvu v rámci velkých znaků.</span><span class="sxs-lookup"><span data-stu-id="fad77-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="fad77-113">mimo Všechny hodnoty příznaků použité u člena.</span><span class="sxs-lookup"><span data-stu-id="fad77-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="fad77-114">mimo Ukazatel na binární podpis metadat člena.</span><span class="sxs-lookup"><span data-stu-id="fad77-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="fad77-115">mimo Velikost v bajtech `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="fad77-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="fad77-116">mimo Ukazatel na relativní virtuální adresu člena.</span><span class="sxs-lookup"><span data-stu-id="fad77-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="fad77-117">mimo Jakékoli příznaky implementace metody přidružené ke členu.</span><span class="sxs-lookup"><span data-stu-id="fad77-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="fad77-118">mimo Příznak, který označuje <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="fad77-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="fad77-119">Je to jedna z hodnot `ELEMENT_TYPE_*`.</span><span class="sxs-lookup"><span data-stu-id="fad77-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="fad77-120">mimo Hodnota konstanty řetězce vrácená tímto členem.</span><span class="sxs-lookup"><span data-stu-id="fad77-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="fad77-121">mimo Velikost ve znacích `ppValue`nebo nula, pokud `ppValue` nedrží řetězec.</span><span class="sxs-lookup"><span data-stu-id="fad77-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fad77-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fad77-122">Requirements</span></span>  
 <span data-ttu-id="fad77-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fad77-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fad77-124">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fad77-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fad77-125">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fad77-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fad77-126">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fad77-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fad77-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fad77-127">See also</span></span>

- [<span data-ttu-id="fad77-128">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fad77-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="fad77-129">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fad77-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
