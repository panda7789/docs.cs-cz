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
ms.openlocfilehash: fa4f1f57cb8fe1ca81bbad6438a88bb43c48e7bf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008076"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="62683-102">IMetaDataAssemblyEmit::SetExportedTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="62683-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="62683-103">Upraví zadanou `ExportedType` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="62683-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62683-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62683-104">Syntax</span></span>  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62683-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="62683-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="62683-106">pro Token metadat, který určuje `ExportedType` strukturu metadat, která má být upravena.</span><span class="sxs-lookup"><span data-stu-id="62683-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="62683-107">pro Token, typu `File` , `AssemblyRef` nebo `ExportedType` , který určuje, jak je tento typ implementován.</span><span class="sxs-lookup"><span data-stu-id="62683-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="62683-108">pro Token, na `TypeDef` který se odkazuje v souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="62683-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="62683-109">pro Bitová kombinace hodnot, které určují atributy typu.</span><span class="sxs-lookup"><span data-stu-id="62683-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62683-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="62683-110">Remarks</span></span>  
 <span data-ttu-id="62683-111">Chcete-li vytvořit `ExportedType` strukturu metadat, použijte metodu [IMetaDataAssemblyEmit::D efineexportedtype](imetadataassemblyemit-defineexportedtype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="62683-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62683-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62683-112">Requirements</span></span>  
 <span data-ttu-id="62683-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62683-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62683-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="62683-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="62683-115">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="62683-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="62683-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62683-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62683-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="62683-117">See also</span></span>

- [<span data-ttu-id="62683-118">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62683-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
