---
title: IMetaDataAssemblyImport::FindExportedTypeByName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindExportedTypeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindExportedTypeByName
helpviewer_keywords:
- FindExportedTypeByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindExportedTypeByName method [.NET Framework metadata]
ms.assetid: 46264b2c-574d-4dde-aafc-77187a104fdd
topic_type:
- apiref
ms.openlocfilehash: ac6de9a16fad6ba9d14f3960ddd28c42c111f254
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009389"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="e2b8a-102">IMetaDataAssemblyImport::FindExportedTypeByName – metoda</span><span class="sxs-lookup"><span data-stu-id="e2b8a-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="e2b8a-103">Získá ukazatel na exportovaný typ, který je dán názvem a nadřazeným typem.</span><span class="sxs-lookup"><span data-stu-id="e2b8a-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2b8a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2b8a-104">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,
    [in]  mdToken           mdtExportedType,
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2b8a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2b8a-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="e2b8a-106">pro Název exportovaného typu.</span><span class="sxs-lookup"><span data-stu-id="e2b8a-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="e2b8a-107">pro Token metadat pro ohraničující třídu exportovaného typu</span><span class="sxs-lookup"><span data-stu-id="e2b8a-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="e2b8a-108">Tato hodnota je `mdExportedTypeNil` , pokud požadovaný exportovaný typ není vnořený typ.</span><span class="sxs-lookup"><span data-stu-id="e2b8a-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="e2b8a-109">mimo Ukazatel na `mdExportedType` token, který představuje exportovaný typ.</span><span class="sxs-lookup"><span data-stu-id="e2b8a-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2b8a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2b8a-110">Remarks</span></span>  
 <span data-ttu-id="e2b8a-111">`FindExportedTypeByName`Metoda používá ke zjišťování odkazů standardní pravidla zaměstnaná modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="e2b8a-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2b8a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2b8a-112">Requirements</span></span>  
 <span data-ttu-id="e2b8a-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2b8a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2b8a-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e2b8a-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e2b8a-115">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="e2b8a-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e2b8a-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2b8a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2b8a-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2b8a-117">See also</span></span>

- [<span data-ttu-id="e2b8a-118">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2b8a-118">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="e2b8a-119">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="e2b8a-119">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
