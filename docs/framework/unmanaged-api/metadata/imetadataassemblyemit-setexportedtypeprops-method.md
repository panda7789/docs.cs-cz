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
ms.openlocfilehash: dd1d6f1da6e49837eebd9356500f403c199b011b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177855"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="61de3-102">IMetaDataAssemblyEmit::SetExportedTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="61de3-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="61de3-103">Upraví zadanou `ExportedType` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="61de3-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61de3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61de3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61de3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="61de3-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="61de3-106">[v] Token metadat, který určuje `ExportedType` strukturu metadat, která má být změněna.</span><span class="sxs-lookup"><span data-stu-id="61de3-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="61de3-107">[v] Token typu `File`, `AssemblyRef`, `ExportedType`nebo , který určuje, jak je tento typ implementován.</span><span class="sxs-lookup"><span data-stu-id="61de3-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="61de3-108">[v] Token `TypeDef` odkazovaný v souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="61de3-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="61de3-109">[v] Bitová kombinace hodnot, které určují atributy typu.</span><span class="sxs-lookup"><span data-stu-id="61de3-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61de3-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61de3-110">Remarks</span></span>  
 <span data-ttu-id="61de3-111">Chcete-li `ExportedType` vytvořit strukturu metadat, použijte metodu [IMetaDataAssemblyEmit::DefineExportedType.](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)</span><span class="sxs-lookup"><span data-stu-id="61de3-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61de3-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="61de3-112">Requirements</span></span>  
 <span data-ttu-id="61de3-113">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61de3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61de3-114">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="61de3-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="61de3-115">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="61de3-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="61de3-116">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61de3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61de3-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="61de3-117">See also</span></span>

- [<span data-ttu-id="61de3-118">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61de3-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
