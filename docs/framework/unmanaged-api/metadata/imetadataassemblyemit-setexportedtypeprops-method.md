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
ms.openlocfilehash: ae682c354a7a5188611b103008a3e18f8d821260
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431938"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="a2d31-102">IMetaDataAssemblyEmit::SetExportedTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="a2d31-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="a2d31-103">Upraví zadanou `ExportedType` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="a2d31-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2d31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2d31-104">Syntax</span></span>  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2d31-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2d31-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="a2d31-106">pro Token metadat, který určuje `ExportedType` strukturu metadat, která se má upravit.</span><span class="sxs-lookup"><span data-stu-id="a2d31-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="a2d31-107">pro Token typu `File`, `AssemblyRef`nebo `ExportedType`, který určuje, jak je tento typ implementován.</span><span class="sxs-lookup"><span data-stu-id="a2d31-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="a2d31-108">pro Token `TypeDef`, na který se odkazuje v souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="a2d31-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="a2d31-109">pro Bitová kombinace hodnot, které určují atributy typu.</span><span class="sxs-lookup"><span data-stu-id="a2d31-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2d31-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a2d31-110">Remarks</span></span>  
 <span data-ttu-id="a2d31-111">Chcete-li vytvořit `ExportedType` struktury metadat, použijte metodu [IMetaDataAssemblyEmit::D efineexportedtype](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a2d31-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2d31-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a2d31-112">Requirements</span></span>  
 <span data-ttu-id="a2d31-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2d31-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2d31-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a2d31-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a2d31-115">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="a2d31-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a2d31-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2d31-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2d31-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a2d31-117">See also</span></span>

- [<span data-ttu-id="a2d31-118">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a2d31-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
