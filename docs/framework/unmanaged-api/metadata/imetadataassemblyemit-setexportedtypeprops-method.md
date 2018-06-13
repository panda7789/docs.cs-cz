---
title: IMetaDataAssemblyEmit::SetExportedTypeProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8643a4d207fb570195caa00a1ac659c78c2ff2b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445063"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="f02f1-102">IMetaDataAssemblyEmit::SetExportedTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="f02f1-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="f02f1-103">Upraví zadaný `ExportedType` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="f02f1-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f02f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f02f1-104">Syntax</span></span>  
  
```  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f02f1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f02f1-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="f02f1-106">[v] Metadata token, který určuje `ExportedType` strukturu metadat má být změněn.</span><span class="sxs-lookup"><span data-stu-id="f02f1-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="f02f1-107">[v] Token, typu `File`, `AssemblyRef`, nebo `ExportedType`, který určuje, jak je implementována tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="f02f1-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="f02f1-108">[v] `TypeDef` Token v souboru kódu odkazovat.</span><span class="sxs-lookup"><span data-stu-id="f02f1-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="f02f1-109">[v] Bitová kombinace hodnot, které určují atributy typu.</span><span class="sxs-lookup"><span data-stu-id="f02f1-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f02f1-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f02f1-110">Remarks</span></span>  
 <span data-ttu-id="f02f1-111">Chcete-li vytvořit `ExportedType` strukturu metadat, použijte [imetadataassemblyemit::defineexportedtype –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="f02f1-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f02f1-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f02f1-112">Requirements</span></span>  
 <span data-ttu-id="f02f1-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f02f1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f02f1-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f02f1-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f02f1-115">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f02f1-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f02f1-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f02f1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f02f1-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="f02f1-117">See Also</span></span>  
 [<span data-ttu-id="f02f1-118">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f02f1-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
