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
ms.openlocfilehash: 5b4b0682b2bddff96cb3d720900ed3aa39f06f9d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431849"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="be750-102">IMetaDataEmit::DefineImportType – metoda</span><span class="sxs-lookup"><span data-stu-id="be750-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="be750-103">Vytvoří odkaz na zadaný typ, který je definován mimo aktuální rozsah, a definuje token pro tento odkaz.</span><span class="sxs-lookup"><span data-stu-id="be750-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be750-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be750-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="be750-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="be750-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="be750-106">pro Rozhraní [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) , které představuje sestavení, ze kterého je importován cílový typ.</span><span class="sxs-lookup"><span data-stu-id="be750-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="be750-107">pro Pole, které obsahuje hodnotu hash pro sestavení určené parametrem `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="be750-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="be750-108">pro Počet bajtů v poli `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="be750-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="be750-109">pro Rozhraní [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) , které představuje obor metadat, ze kterého je importován cílový typ.</span><span class="sxs-lookup"><span data-stu-id="be750-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="be750-110">pro Token `mdTypeDef`, který určuje cílový typ.</span><span class="sxs-lookup"><span data-stu-id="be750-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="be750-111">pro Rozhraní [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) představující sestavení, do kterého se naimportuje cílový typ.</span><span class="sxs-lookup"><span data-stu-id="be750-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="be750-112">mimo Token `mdTypeRef`, který je definován v aktuálním oboru pro odkaz na typ.</span><span class="sxs-lookup"><span data-stu-id="be750-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be750-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="be750-113">Remarks</span></span>  
 <span data-ttu-id="be750-114">Před voláním metody [IMetaDataEmit::D efineimportmember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) lze pomocí metody `DefineImportType` vytvořit odkaz na typ v aktuálním oboru pro nadřazenou třídu člena nebo pro nadřazené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="be750-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be750-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be750-115">Requirements</span></span>  
 <span data-ttu-id="be750-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be750-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be750-117">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="be750-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be750-118">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="be750-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be750-119">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be750-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be750-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be750-120">See also</span></span>

- [<span data-ttu-id="be750-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be750-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="be750-122">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be750-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
