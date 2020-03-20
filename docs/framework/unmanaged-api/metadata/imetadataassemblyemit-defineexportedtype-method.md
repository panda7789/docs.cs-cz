---
title: IMetaDataAssemblyEmit::DefineExportedType – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
ms.openlocfilehash: 388f227377ddf73fe1297e1c777bb1c0607c13d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177882"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="55ba8-102">IMetaDataAssemblyEmit::DefineExportedType – metoda</span><span class="sxs-lookup"><span data-stu-id="55ba8-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>
<span data-ttu-id="55ba8-103">Vytvoří `ExportedType` strukturu obsahující metadata pro zadaný exportovaný typ a vrátí přidružený token metadat.</span><span class="sxs-lookup"><span data-stu-id="55ba8-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55ba8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55ba8-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55ba8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="55ba8-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="55ba8-106">[v] Název typu, který má být exportován.</span><span class="sxs-lookup"><span data-stu-id="55ba8-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="55ba8-107">Pro verzi 1.1 za běhu společného jazyka musí název exportovaného typu `TypeDef` přesně odpovídat názvu uvedenému v pro typ.</span><span class="sxs-lookup"><span data-stu-id="55ba8-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="55ba8-108">[v] Token určující, kde je implementován exportovaný typ.</span><span class="sxs-lookup"><span data-stu-id="55ba8-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="55ba8-109">Platné hodnoty a jejich přidružené významy jsou:</span><span class="sxs-lookup"><span data-stu-id="55ba8-109">The valid values and their associated meanings are:</span></span>  
  
- <span data-ttu-id="55ba8-110">`mdFile`Typ je implementován v jiném souboru v rámci tohoto sestavení.</span><span class="sxs-lookup"><span data-stu-id="55ba8-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
- <span data-ttu-id="55ba8-111">`mdAssemblyRef`Typ je implementován v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="55ba8-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
- <span data-ttu-id="55ba8-112">`mdExportedTYpe`Typ je vnořen do jiného typu.</span><span class="sxs-lookup"><span data-stu-id="55ba8-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
- <span data-ttu-id="55ba8-113">`mdFileNil`Typ je ve stejném souboru jako manifest a není vnořený typ.</span><span class="sxs-lookup"><span data-stu-id="55ba8-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="55ba8-114">[v] Token metadat, který určuje typ, který má být exportován.</span><span class="sxs-lookup"><span data-stu-id="55ba8-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="55ba8-115">Tato hodnota je `TypeDef` zadána v tabulce v souboru, který implementuje typ a je relevantní pouze v případě, že tento soubor je v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="55ba8-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="55ba8-116">[v] Bitová kombinace hodnot výčtu [CorTypeAttr,](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) které definují nastavení vlastností exportovaného typu.</span><span class="sxs-lookup"><span data-stu-id="55ba8-116">[in] A bitwise combination of [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="55ba8-117">[out] Ukazatel na vrácený token metadat, který označuje exportovaný typ.</span><span class="sxs-lookup"><span data-stu-id="55ba8-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55ba8-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="55ba8-118">Remarks</span></span>  
 <span data-ttu-id="55ba8-119">Struktura `ExportedType` metadat musí být definována pro každý typ, který je vystaven tímto sestavením a který je implementován v modulu než ten, který obsahuje manifest.</span><span class="sxs-lookup"><span data-stu-id="55ba8-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55ba8-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="55ba8-120">Requirements</span></span>  
 <span data-ttu-id="55ba8-121">**Platforma:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55ba8-121">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55ba8-122">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="55ba8-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="55ba8-123">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="55ba8-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="55ba8-124">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55ba8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55ba8-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="55ba8-125">See also</span></span>

- [<span data-ttu-id="55ba8-126">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="55ba8-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
