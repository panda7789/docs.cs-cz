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
ms.openlocfilehash: d93763da2afbbdb1e738c802ba172e9f16e5f7af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448455"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="90288-102">IMetaDataImport::GetMemberProps – metoda</span><span class="sxs-lookup"><span data-stu-id="90288-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="90288-103">Získá informace o metadatech, včetně názvu, binární podpisu a relativní virtuální adresy, nástroje <xref:System.Type> člen odkazuje token Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="90288-103">Gets metadata information, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90288-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90288-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="90288-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="90288-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="90288-106">[v] Token, který odkazuje na člena získat související metadata pro.</span><span class="sxs-lookup"><span data-stu-id="90288-106">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="90288-107">[out] Ukazatel na metadata token, který představuje třídu člena.</span><span class="sxs-lookup"><span data-stu-id="90288-107">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="90288-108">[out] Název člena.</span><span class="sxs-lookup"><span data-stu-id="90288-108">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="90288-109">[v] Velikost v široké znaky `szMember` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="90288-109">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="90288-110">[out] Velikost v široké znaky vrácený název.</span><span class="sxs-lookup"><span data-stu-id="90288-110">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="90288-111">[out] Veškeré příznak hodnoty, použijí se členem.</span><span class="sxs-lookup"><span data-stu-id="90288-111">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="90288-112">[out] Ukazatel na podpis binární metadata člena.</span><span class="sxs-lookup"><span data-stu-id="90288-112">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="90288-113">[out] Velikost v bajtech `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="90288-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="90288-114">[out] Ukazatel s relativní virtuální adresou tohoto člena.</span><span class="sxs-lookup"><span data-stu-id="90288-114">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="90288-115">[out] Žádné příznaky implementace metoda spojených se členem.</span><span class="sxs-lookup"><span data-stu-id="90288-115">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="90288-116">[out] Příznak, který určuje, že <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="90288-116">[out] A flag that marks a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="90288-117">[out] Hodnota konstantní řetězec vrácený tohoto člena.</span><span class="sxs-lookup"><span data-stu-id="90288-117">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="90288-118">[out] Velikost ve znacích `ppValue`, nebo nula, pokud `ppValue` neobsahuje řetězec.</span><span class="sxs-lookup"><span data-stu-id="90288-118">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90288-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90288-119">Requirements</span></span>  
 <span data-ttu-id="90288-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90288-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90288-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="90288-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="90288-122">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="90288-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="90288-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90288-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90288-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="90288-124">See Also</span></span>  
 [<span data-ttu-id="90288-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90288-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="90288-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90288-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
