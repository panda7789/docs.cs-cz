---
title: "IMetaDataImport::GetMemberProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetMemberProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 543929390977fc593e86947feece06f43bc0cad6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="5d9af-102">IMetaDataImport::GetMemberProps – metoda</span><span class="sxs-lookup"><span data-stu-id="5d9af-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="5d9af-103">Získá informace o metadatech, včetně názvu, binární podpisu a relativní virtuální adresy, nástroje <xref:System.Type> člen odkazuje token Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="5d9af-103">Gets metadata information, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d9af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d9af-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="5d9af-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d9af-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="5d9af-106">[v] Token, který odkazuje na člena získat související metadata pro.</span><span class="sxs-lookup"><span data-stu-id="5d9af-106">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="5d9af-107">[out] Ukazatel na metadata token, který představuje třídu člena.</span><span class="sxs-lookup"><span data-stu-id="5d9af-107">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="5d9af-108">[out] Název člena.</span><span class="sxs-lookup"><span data-stu-id="5d9af-108">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="5d9af-109">[v] Velikost v široké znaky `szMember` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5d9af-109">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="5d9af-110">[out] Velikost v široké znaky vrácený název.</span><span class="sxs-lookup"><span data-stu-id="5d9af-110">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="5d9af-111">[out] Veškeré příznak hodnoty, použijí se členem.</span><span class="sxs-lookup"><span data-stu-id="5d9af-111">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="5d9af-112">[out] Ukazatel na podpis binární metadata člena.</span><span class="sxs-lookup"><span data-stu-id="5d9af-112">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="5d9af-113">[out] Velikost v bajtech `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="5d9af-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="5d9af-114">[out] Ukazatel s relativní virtuální adresou tohoto člena.</span><span class="sxs-lookup"><span data-stu-id="5d9af-114">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="5d9af-115">[out] Žádné příznaky implementace metoda spojených se členem.</span><span class="sxs-lookup"><span data-stu-id="5d9af-115">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="5d9af-116">[out] Příznak, který určuje, že <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="5d9af-116">[out] A flag that marks a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="5d9af-117">[out] Hodnota konstantní řetězec vrácený tohoto člena.</span><span class="sxs-lookup"><span data-stu-id="5d9af-117">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="5d9af-118">[out] Velikost ve znacích `ppValue`, nebo nula, pokud `ppValue` neobsahuje řetězec.</span><span class="sxs-lookup"><span data-stu-id="5d9af-118">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d9af-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d9af-119">Requirements</span></span>  
 <span data-ttu-id="5d9af-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d9af-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d9af-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5d9af-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5d9af-122">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5d9af-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5d9af-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d9af-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d9af-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d9af-124">See Also</span></span>  
 [<span data-ttu-id="5d9af-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d9af-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="5d9af-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d9af-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
