---
title: "IMetaDataEmit::DefineImportType – metoda"
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
- IMetaDataEmit.DefineImportType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportType
helpviewer_keywords:
- DefineImportType method [.NET Framework metadata]
- IMetaDataEmit::DefineImportType method [.NET Framework metadata]
ms.assetid: 37fd27af-8062-4904-ace4-51bb78ec600a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1fee13c88cc39398808ad1ff481e602d63e8f39f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="d0f5e-102">IMetaDataEmit::DefineImportType – metoda</span><span class="sxs-lookup"><span data-stu-id="d0f5e-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="d0f5e-103">Vytvoří odkaz na zadaný typ, který je definován v aktuálním oboru a definuje token pro tento odkaz.</span><span class="sxs-lookup"><span data-stu-id="d0f5e-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0f5e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0f5e-104">Syntax</span></span>  
  
```  
HRESULT DefineImportType (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,    
    [in]  IMetaDataImport          *pImport,   
    [in]  mdTypeDef                tdImport,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [out] mdTypeRef                *ptr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0f5e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0f5e-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="d0f5e-106">[v] [Imetadataassemblyimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní, které představuje sestavení, ve kterém je naimportována na typ cíle.</span><span class="sxs-lookup"><span data-stu-id="d0f5e-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="d0f5e-107">[v] Pole, které obsahuje hodnotu hash pro sestavení určeného `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="d0f5e-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="d0f5e-108">[v] Počet bajtů `pbHashValue` pole.</span><span class="sxs-lookup"><span data-stu-id="d0f5e-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="d0f5e-109">[v] [Imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) rozhraní, které představuje metadata oboru, ze kterého je naimportována na typ cíle.</span><span class="sxs-lookup"><span data-stu-id="d0f5e-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="d0f5e-110">[v] `mdTypeDef` Token, který určuje typ cíle.</span><span class="sxs-lookup"><span data-stu-id="d0f5e-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="d0f5e-111">[v] [Imetadataassemblyemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) rozhraní, které představuje sestavení, do kterého je naimportována na typ cíle.</span><span class="sxs-lookup"><span data-stu-id="d0f5e-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="d0f5e-112">[out] `mdTypeRef` Token, který je definován v aktuálním oboru pro odkaz na typ.</span><span class="sxs-lookup"><span data-stu-id="d0f5e-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0f5e-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d0f5e-113">Remarks</span></span>  
 <span data-ttu-id="d0f5e-114">Před voláním [imetadataemit::defineimportmember –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) metodu, můžete použít `DefineImportType` metodu pro vytvoření odkaz na typ v aktuálním oboru pro nadřazené třídy nebo rozhraní nadřazeného člena.</span><span class="sxs-lookup"><span data-stu-id="d0f5e-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0f5e-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0f5e-115">Requirements</span></span>  
 <span data-ttu-id="d0f5e-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0f5e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0f5e-117">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d0f5e-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d0f5e-118">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d0f5e-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0f5e-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0f5e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0f5e-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0f5e-120">See Also</span></span>  
 [<span data-ttu-id="d0f5e-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0f5e-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="d0f5e-122">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0f5e-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
