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
ms.openlocfilehash: 6825a5198976cc7ab2c04ebd6e782418dcf4a8f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177684"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="68b3a-102">IMetaDataEmit::DefineImportType – metoda</span><span class="sxs-lookup"><span data-stu-id="68b3a-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="68b3a-103">Vytvoří odkaz na zadaný typ, který je definován mimo aktuální obor, a definuje token pro tento odkaz.</span><span class="sxs-lookup"><span data-stu-id="68b3a-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68b3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68b3a-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="68b3a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="68b3a-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="68b3a-106">[v] Rozhraní [IMetaDataAssemblyImport,](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) které představuje sestavení, ze kterého je importován cílový typ.</span><span class="sxs-lookup"><span data-stu-id="68b3a-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="68b3a-107">[v] Pole, které obsahuje hash pro `pAssemImport`sestavení určené .</span><span class="sxs-lookup"><span data-stu-id="68b3a-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="68b3a-108">[v] Počet bajtů v `pbHashValue` poli.</span><span class="sxs-lookup"><span data-stu-id="68b3a-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="68b3a-109">[v] Rozhraní [IMetaDataImport,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) které představuje obor metadat, ze kterého je importován cílový typ.</span><span class="sxs-lookup"><span data-stu-id="68b3a-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="68b3a-110">[v] Token, `mdTypeDef` který určuje cílový typ.</span><span class="sxs-lookup"><span data-stu-id="68b3a-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="68b3a-111">[v] Rozhraní [IMetaDataAssemblyEmit,](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) které představuje sestavení, do kterého je importován cílový typ.</span><span class="sxs-lookup"><span data-stu-id="68b3a-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="68b3a-112">[out] Token, `mdTypeRef` který je definován v aktuálním oboru pro odkaz na typ.</span><span class="sxs-lookup"><span data-stu-id="68b3a-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68b3a-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68b3a-113">Remarks</span></span>  
 <span data-ttu-id="68b3a-114">Před voláním metody [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) můžete `DefineImportType` použít metodu k vytvoření odkazu na typ v aktuálním oboru pro nadřazenou třídu člena nebo nadřazené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="68b3a-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68b3a-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="68b3a-115">Requirements</span></span>  
 <span data-ttu-id="68b3a-116">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68b3a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68b3a-117">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="68b3a-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="68b3a-118">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="68b3a-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68b3a-119">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68b3a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68b3a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="68b3a-120">See also</span></span>

- [<span data-ttu-id="68b3a-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68b3a-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="68b3a-122">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68b3a-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
