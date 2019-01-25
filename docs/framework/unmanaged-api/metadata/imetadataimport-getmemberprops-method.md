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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98d7be5adc81cff09b121265e7d5b5f712122607
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611407"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="65696-102">IMetaDataImport::GetMemberProps – metoda</span><span class="sxs-lookup"><span data-stu-id="65696-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="65696-103">Získá informace o metadata, včetně názvu, binární podpis a relativní virtuální adresu, <xref:System.Type> odkazuje token metadat zadaného člena.</span><span class="sxs-lookup"><span data-stu-id="65696-103">Gets metadata information, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65696-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65696-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="65696-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65696-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="65696-106">[in] Token, který odkazuje na člen, který chcete získat související metadata pro.</span><span class="sxs-lookup"><span data-stu-id="65696-106">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="65696-107">[out] Ukazatel na token metadat, který představuje třídu člena.</span><span class="sxs-lookup"><span data-stu-id="65696-107">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="65696-108">[out] Název člena.</span><span class="sxs-lookup"><span data-stu-id="65696-108">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="65696-109">[in] Velikost v širokých znaků `szMember` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="65696-109">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="65696-110">[out] Velikost v široké znaky vrácený název.</span><span class="sxs-lookup"><span data-stu-id="65696-110">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="65696-111">[out] Žádné příznak hodnoty použité k členu.</span><span class="sxs-lookup"><span data-stu-id="65696-111">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="65696-112">[out] Ukazatel na binární metadat podpisu člena.</span><span class="sxs-lookup"><span data-stu-id="65696-112">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="65696-113">[out] Velikost v bajtech `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="65696-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="65696-114">[out] Ukazatel na relativní virtuální adresu člena.</span><span class="sxs-lookup"><span data-stu-id="65696-114">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="65696-115">[out] Žádné příznaky implementace spojených se členem.</span><span class="sxs-lookup"><span data-stu-id="65696-115">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="65696-116">[out] Příznak, který označuje <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="65696-116">[out] A flag that marks a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="65696-117">[out] Hodnota konstanty typu řetězec vrácený tohoto člena.</span><span class="sxs-lookup"><span data-stu-id="65696-117">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="65696-118">[out] Velikost ve znacích `ppValue`, nebo nula, pokud `ppValue` neobsahuje řetězec.</span><span class="sxs-lookup"><span data-stu-id="65696-118">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65696-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65696-119">Requirements</span></span>  
 <span data-ttu-id="65696-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65696-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65696-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="65696-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65696-122">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65696-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="65696-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65696-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65696-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65696-124">See also</span></span>
- [<span data-ttu-id="65696-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65696-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="65696-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65696-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
