---
title: "IMetaDataImport::GetFieldProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7785ea6beaa882e72d200ef559ba75538224091d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="78f6b-102">IMetaDataImport::GetFieldProps – metoda</span><span class="sxs-lookup"><span data-stu-id="78f6b-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="78f6b-103">Získá metadata spojená s polem odkazuje zadaný FieldDef token.</span><span class="sxs-lookup"><span data-stu-id="78f6b-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78f6b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78f6b-104">Syntax</span></span>  
  
```  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,   
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78f6b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78f6b-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="78f6b-106">[v] FieldDef token, který představuje pole, které chcete získat související metadata pro.</span><span class="sxs-lookup"><span data-stu-id="78f6b-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="78f6b-107">[out] Ukazatel na TypeDef token, který představuje typ třídy, která patří pole.</span><span class="sxs-lookup"><span data-stu-id="78f6b-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="78f6b-108">[out] Název pole.</span><span class="sxs-lookup"><span data-stu-id="78f6b-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="78f6b-109">[v] Velikost v široké znaky vyrovnávací paměti pro *szField*.</span><span class="sxs-lookup"><span data-stu-id="78f6b-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="78f6b-110">[out] Skutečná velikost vrácený vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="78f6b-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="78f6b-111">[out] Příznaky přidružená metadata tohoto pole.</span><span class="sxs-lookup"><span data-stu-id="78f6b-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="78f6b-112">[v] Ukazatel na hodnotu binární metadata, která popisuje pole.</span><span class="sxs-lookup"><span data-stu-id="78f6b-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="78f6b-113">[out] Velikost v bajtech `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="78f6b-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="78f6b-114">[out] Příznak, který určuje typ hodnoty pole.</span><span class="sxs-lookup"><span data-stu-id="78f6b-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="78f6b-115">[out] Konstantní hodnota pro pole.</span><span class="sxs-lookup"><span data-stu-id="78f6b-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="78f6b-116">[out] Velikost v znaků z `ppValue`, nebo nula, pokud neexistuje žádný řetězec.</span><span class="sxs-lookup"><span data-stu-id="78f6b-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78f6b-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78f6b-117">Requirements</span></span>  
 <span data-ttu-id="78f6b-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78f6b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78f6b-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="78f6b-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="78f6b-120">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78f6b-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="78f6b-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78f6b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78f6b-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="78f6b-122">See Also</span></span>  
 [<span data-ttu-id="78f6b-123">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78f6b-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="78f6b-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78f6b-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
