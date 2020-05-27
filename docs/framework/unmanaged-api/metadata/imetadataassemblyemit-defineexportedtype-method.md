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
ms.openlocfilehash: 81d6c972b53221ee53cbcf31639d65c30858b48b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008154"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="73daa-102">IMetaDataAssemblyEmit::DefineExportedType – metoda</span><span class="sxs-lookup"><span data-stu-id="73daa-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>
<span data-ttu-id="73daa-103">Vytvoří `ExportedType` strukturu obsahující metadata pro zadaný exportovaný typ a vrátí přidružený token metadat.</span><span class="sxs-lookup"><span data-stu-id="73daa-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73daa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73daa-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73daa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73daa-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="73daa-106">pro Název typu, který má být exportován.</span><span class="sxs-lookup"><span data-stu-id="73daa-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="73daa-107">Pro verzi 1,1 modulu CLR musí název exportovaného typu přesně odpovídat názvu uvedenému v poli `TypeDef` pro typ.</span><span class="sxs-lookup"><span data-stu-id="73daa-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="73daa-108">pro Token určující, kde je implementován exportovaný typ.</span><span class="sxs-lookup"><span data-stu-id="73daa-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="73daa-109">Platné hodnoty a jejich přidružené významy jsou:</span><span class="sxs-lookup"><span data-stu-id="73daa-109">The valid values and their associated meanings are:</span></span>  
  
- <span data-ttu-id="73daa-110">`mdFile`Typ je implementován v jiném souboru v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="73daa-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
- <span data-ttu-id="73daa-111">`mdAssemblyRef`Typ je implementován v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="73daa-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
- <span data-ttu-id="73daa-112">`mdExportedTYpe`Typ je vnořen v jiném typu.</span><span class="sxs-lookup"><span data-stu-id="73daa-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
- <span data-ttu-id="73daa-113">`mdFileNil`Typ je ve stejném souboru jako manifest a není vnořený typ.</span><span class="sxs-lookup"><span data-stu-id="73daa-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="73daa-114">pro Token metadat, který určuje typ, který má být exportován.</span><span class="sxs-lookup"><span data-stu-id="73daa-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="73daa-115">Tato hodnota je zadána v `TypeDef` tabulce v souboru, který implementuje typ a je relevantní pouze v případě, že tento soubor je v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="73daa-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="73daa-116">pro Bitová kombinace hodnot výčtu [CorTypeAttr –](cortypeattr-enumeration.md) , která definuje nastavení vlastností pro exportovaný typ.</span><span class="sxs-lookup"><span data-stu-id="73daa-116">[in] A bitwise combination of [CorTypeAttr](cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="73daa-117">mimo Ukazatel na vrácený token metadat, který označuje exportovaný typ.</span><span class="sxs-lookup"><span data-stu-id="73daa-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73daa-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73daa-118">Remarks</span></span>  
 <span data-ttu-id="73daa-119">`ExportedType`Struktura metadat musí být definována pro každý typ, který je vystaven tímto sestavením a který je implementován v jiném modulu než ten, který obsahuje manifest.</span><span class="sxs-lookup"><span data-stu-id="73daa-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73daa-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73daa-120">Requirements</span></span>  
 <span data-ttu-id="73daa-121">**Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73daa-121">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73daa-122">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="73daa-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="73daa-123">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="73daa-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="73daa-124">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73daa-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73daa-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="73daa-125">See also</span></span>

- [<span data-ttu-id="73daa-126">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73daa-126">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
