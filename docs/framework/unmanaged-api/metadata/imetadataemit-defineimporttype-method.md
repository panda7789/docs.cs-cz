---
title: IMetaDataEmit::DefineImportType – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9ac7bc865371744f6742622243398a506607373c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469128"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="70757-102">IMetaDataEmit::DefineImportType – metoda</span><span class="sxs-lookup"><span data-stu-id="70757-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="70757-103">Vytvoří odkaz na zadaný typ definovaný vně aktuálního oboru, který definuje token pro tento odkaz.</span><span class="sxs-lookup"><span data-stu-id="70757-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70757-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70757-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="70757-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70757-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="70757-106">[in] [Imetadataassemblyimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní, které představuje sestavení, ze kterého se importují cílového typu.</span><span class="sxs-lookup"><span data-stu-id="70757-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="70757-107">[in] Pole, která obsahuje hodnotu hash pro sestavení určené parametrem `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="70757-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="70757-108">[in] Počet bajtů `pbHashValue` pole.</span><span class="sxs-lookup"><span data-stu-id="70757-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="70757-109">[in] [Imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) rozhraní, které představuje obor metadat, ze kterého se importují cílového typu.</span><span class="sxs-lookup"><span data-stu-id="70757-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="70757-110">[in] `mdTypeDef` Token, který určuje typ cíle.</span><span class="sxs-lookup"><span data-stu-id="70757-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="70757-111">[in] [Imetadataassemblyemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) rozhraní, které představuje sestavení, do kterého se importují cílového typu.</span><span class="sxs-lookup"><span data-stu-id="70757-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="70757-112">[out] `mdTypeRef` Token, který je definován v oboru pro typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="70757-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70757-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70757-113">Remarks</span></span>  
 <span data-ttu-id="70757-114">Před voláním [imetadataemit::defineimportmember –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) metodu, můžete použít `DefineImportType` metodu pro vytvoření odkazu typu v aktuálním oboru pro nadřazené třídu nebo rozhraní nadřazeného člena.</span><span class="sxs-lookup"><span data-stu-id="70757-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70757-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70757-115">Requirements</span></span>  
 <span data-ttu-id="70757-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70757-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70757-117">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="70757-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="70757-118">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="70757-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70757-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70757-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70757-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70757-120">See also</span></span>
- [<span data-ttu-id="70757-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70757-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="70757-122">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70757-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
