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
ms.openlocfilehash: 83dec9b6ed3b1e538e0f1b7d13a33b8bdbc1cf54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777725"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="f15dc-102">IMetaDataImport::GetMemberProps – metoda</span><span class="sxs-lookup"><span data-stu-id="f15dc-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="f15dc-103">Získá informace uložené v metadatech pro definici zadaného člena, včetně názvu, binární podpis a relativní virtuální adresu, <xref:System.Type> odkazuje token metadat zadaného člena.</span><span class="sxs-lookup"><span data-stu-id="f15dc-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="f15dc-104">Toto je jednoduchý Pomocná metoda: Pokud *mb* typu MethodDef, pak je **getmethodprops –** se nazývá; Pokud *mb* FieldDef, pak je **getfieldprops –** je volána.</span><span class="sxs-lookup"><span data-stu-id="f15dc-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="f15dc-105">Informace najdete v těchto jiných metod podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="f15dc-105">See these other methods for details.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="f15dc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f15dc-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f15dc-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f15dc-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="f15dc-108">[in] Token, který odkazuje na člen, který chcete získat související metadata pro.</span><span class="sxs-lookup"><span data-stu-id="f15dc-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="f15dc-109">[out] Ukazatel na token metadat, který představuje třídu člena.</span><span class="sxs-lookup"><span data-stu-id="f15dc-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="f15dc-110">[out] Název člena.</span><span class="sxs-lookup"><span data-stu-id="f15dc-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="f15dc-111">[in] Velikost v širokých znaků `szMember` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="f15dc-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="f15dc-112">[out] Velikost v široké znaky vrácený název.</span><span class="sxs-lookup"><span data-stu-id="f15dc-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="f15dc-113">[out] Žádné příznak hodnoty použité k členu.</span><span class="sxs-lookup"><span data-stu-id="f15dc-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="f15dc-114">[out] Ukazatel na binární metadat podpisu člena.</span><span class="sxs-lookup"><span data-stu-id="f15dc-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="f15dc-115">[out] Velikost v bajtech `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="f15dc-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="f15dc-116">[out] Ukazatel na relativní virtuální adresu člena.</span><span class="sxs-lookup"><span data-stu-id="f15dc-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="f15dc-117">[out] Žádné příznaky implementace spojených se členem.</span><span class="sxs-lookup"><span data-stu-id="f15dc-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="f15dc-118">[out] Příznak, který označuje <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="f15dc-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="f15dc-119">Představuje jednu ze `ELEMENT_TYPE_*` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f15dc-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="f15dc-120">[out] Hodnota konstanty typu řetězec vrácený tohoto člena.</span><span class="sxs-lookup"><span data-stu-id="f15dc-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="f15dc-121">[out] Velikost ve znacích `ppValue`, nebo nula, pokud `ppValue` neobsahuje řetězec.</span><span class="sxs-lookup"><span data-stu-id="f15dc-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f15dc-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f15dc-122">Requirements</span></span>  
 <span data-ttu-id="f15dc-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f15dc-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f15dc-124">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f15dc-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f15dc-125">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f15dc-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f15dc-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f15dc-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f15dc-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f15dc-127">See also</span></span>

- [<span data-ttu-id="f15dc-128">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f15dc-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f15dc-129">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f15dc-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
