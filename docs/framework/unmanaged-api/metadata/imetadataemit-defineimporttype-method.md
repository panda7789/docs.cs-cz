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
ms.openlocfilehash: edce5cb93b770fb5730e5a06633ffffacf332f7a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004686"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="54931-102">IMetaDataEmit::DefineImportType – metoda</span><span class="sxs-lookup"><span data-stu-id="54931-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="54931-103">Vytvoří odkaz na zadaný typ, který je definován mimo aktuální rozsah, a definuje token pro tento odkaz.</span><span class="sxs-lookup"><span data-stu-id="54931-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54931-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54931-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="54931-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="54931-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="54931-106">pro Rozhraní [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) , které představuje sestavení, ze kterého je importován cílový typ.</span><span class="sxs-lookup"><span data-stu-id="54931-106">[in] An [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="54931-107">pro Pole, které obsahuje hodnotu hash pro sestavení určené parametrem `pAssemImport` .</span><span class="sxs-lookup"><span data-stu-id="54931-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="54931-108">pro Počet bajtů v `pbHashValue` poli.</span><span class="sxs-lookup"><span data-stu-id="54931-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="54931-109">pro Rozhraní [IMetaDataImport](imetadataimport-interface.md) , které představuje obor metadat, ze kterého je importován cílový typ.</span><span class="sxs-lookup"><span data-stu-id="54931-109">[in] An [IMetaDataImport](imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="54931-110">pro `mdTypeDef`Token, který určuje cílový typ.</span><span class="sxs-lookup"><span data-stu-id="54931-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="54931-111">pro Rozhraní [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) představující sestavení, do kterého se naimportuje cílový typ.</span><span class="sxs-lookup"><span data-stu-id="54931-111">[in] An [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="54931-112">mimo `mdTypeRef`Token, který je definován v aktuálním oboru pro odkaz na typ.</span><span class="sxs-lookup"><span data-stu-id="54931-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54931-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="54931-113">Remarks</span></span>  
 <span data-ttu-id="54931-114">Před voláním metody [IMetaDataEmit::D efineimportmember](imetadataemit-defineimportmember-method.md) lze použít `DefineImportType` metodu pro vytvoření odkazu na typ v aktuálním oboru pro nadřazenou třídu člena nebo pro nadřazené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="54931-114">Prior to calling the [IMetaDataEmit::DefineImportMember](imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54931-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="54931-115">Requirements</span></span>  
 <span data-ttu-id="54931-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54931-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54931-117">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="54931-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="54931-118">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="54931-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54931-119">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54931-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54931-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="54931-120">See also</span></span>

- [<span data-ttu-id="54931-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54931-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="54931-122">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54931-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
