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
ms.openlocfilehash: 40631a15bd07b5aa54488e5d3b99cee751e2e0bd
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748333"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="0dba4-102">IMetaDataImport::GetMemberProps – metoda</span><span class="sxs-lookup"><span data-stu-id="0dba4-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="0dba4-103">Získá informace uložené v metadatech pro definici zadaného člena, včetně názvu, binární podpis a relativní virtuální adresu, <xref:System.Type> odkazuje token metadat zadaného člena.</span><span class="sxs-lookup"><span data-stu-id="0dba4-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="0dba4-104">Toto je jednoduchý Pomocná metoda: Pokud *mb* typu MethodDef, pak je **getmethodprops –** se nazývá; Pokud *mb* FieldDef, pak je **getfieldprops –** je volána.</span><span class="sxs-lookup"><span data-stu-id="0dba4-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="0dba4-105">Informace najdete v těchto jiných metod podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="0dba4-105">See these other methods for details.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="0dba4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0dba4-106">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="0dba4-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="0dba4-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="0dba4-108">[in] Token, který odkazuje na člen, který chcete získat související metadata pro.</span><span class="sxs-lookup"><span data-stu-id="0dba4-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="0dba4-109">[out] Ukazatel na token metadat, který představuje třídu člena.</span><span class="sxs-lookup"><span data-stu-id="0dba4-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="0dba4-110">[out] Název člena.</span><span class="sxs-lookup"><span data-stu-id="0dba4-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="0dba4-111">[in] Velikost v širokých znaků `szMember` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="0dba4-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="0dba4-112">[out] Velikost v široké znaky vrácený název.</span><span class="sxs-lookup"><span data-stu-id="0dba4-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="0dba4-113">[out] Žádné příznak hodnoty použité k členu.</span><span class="sxs-lookup"><span data-stu-id="0dba4-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="0dba4-114">[out] Ukazatel na binární metadat podpisu člena.</span><span class="sxs-lookup"><span data-stu-id="0dba4-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="0dba4-115">[out] Velikost v bajtech `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="0dba4-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="0dba4-116">[out] Ukazatel na relativní virtuální adresu člena.</span><span class="sxs-lookup"><span data-stu-id="0dba4-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="0dba4-117">[out] Žádné příznaky implementace spojených se členem.</span><span class="sxs-lookup"><span data-stu-id="0dba4-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="0dba4-118">[out] Příznak, který označuje <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="0dba4-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="0dba4-119">Představuje jednu ze `ELEMENT_TYPE_*` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0dba4-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="0dba4-120">[out] Hodnota konstanty typu řetězec vrácený tohoto člena.</span><span class="sxs-lookup"><span data-stu-id="0dba4-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="0dba4-121">[out] Velikost ve znacích `ppValue`, nebo nula, pokud `ppValue` neobsahuje řetězec.</span><span class="sxs-lookup"><span data-stu-id="0dba4-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dba4-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0dba4-122">Requirements</span></span>  
 <span data-ttu-id="0dba4-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0dba4-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dba4-124">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0dba4-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0dba4-125">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0dba4-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0dba4-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dba4-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dba4-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0dba4-127">See also</span></span>
- [<span data-ttu-id="0dba4-128">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0dba4-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0dba4-129">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0dba4-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
