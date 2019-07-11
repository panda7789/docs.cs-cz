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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a70c041bc17f58a5e17877dd2e1f2aa2944e689
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777931"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="31631-102">IMetaDataAssemblyImport::FindExportedTypeByName – metoda</span><span class="sxs-lookup"><span data-stu-id="31631-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="31631-103">Získá ukazatel na exportovaný typ daného názvu a nadřazený typ.</span><span class="sxs-lookup"><span data-stu-id="31631-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31631-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31631-104">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31631-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="31631-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="31631-106">[in] Název typu exportované.</span><span class="sxs-lookup"><span data-stu-id="31631-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="31631-107">[in] Token metadat pro nadřazené třídu exportovaného typu.</span><span class="sxs-lookup"><span data-stu-id="31631-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="31631-108">Tato hodnota je `mdExportedTypeNil` Pokud požadovaný export typu není vnořeného typu.</span><span class="sxs-lookup"><span data-stu-id="31631-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="31631-109">[out] Ukazatel `mdExportedType` token, který představuje exportovaného typu.</span><span class="sxs-lookup"><span data-stu-id="31631-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31631-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="31631-110">Remarks</span></span>  
 <span data-ttu-id="31631-111">`FindExportedTypeByName` Metoda používá standardní pravidla náhradník modul common language runtime k vyřešení odkazů.</span><span class="sxs-lookup"><span data-stu-id="31631-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31631-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="31631-112">Requirements</span></span>  
 <span data-ttu-id="31631-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31631-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31631-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="31631-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31631-115">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="31631-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="31631-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31631-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31631-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31631-117">See also</span></span>

- [<span data-ttu-id="31631-118">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="31631-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="31631-119">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="31631-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
