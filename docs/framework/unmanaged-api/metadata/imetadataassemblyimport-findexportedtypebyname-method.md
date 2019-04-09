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
ms.openlocfilehash: 32a7b7b498cc4e52b8be3f43ae52293de380d9f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182257"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="8dca8-102">IMetaDataAssemblyImport::FindExportedTypeByName – metoda</span><span class="sxs-lookup"><span data-stu-id="8dca8-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="8dca8-103">Získá ukazatel na exportovaný typ daného názvu a nadřazený typ.</span><span class="sxs-lookup"><span data-stu-id="8dca8-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dca8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8dca8-104">Syntax</span></span>  
  
```  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8dca8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dca8-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="8dca8-106">[in] Název typu exportované.</span><span class="sxs-lookup"><span data-stu-id="8dca8-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="8dca8-107">[in] Token metadat pro nadřazené třídu exportovaného typu.</span><span class="sxs-lookup"><span data-stu-id="8dca8-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="8dca8-108">Tato hodnota je `mdExportedTypeNil` Pokud požadovaný export typu není vnořeného typu.</span><span class="sxs-lookup"><span data-stu-id="8dca8-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="8dca8-109">[out] Ukazatel `mdExportedType` token, který představuje exportovaného typu.</span><span class="sxs-lookup"><span data-stu-id="8dca8-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8dca8-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8dca8-110">Remarks</span></span>  
 <span data-ttu-id="8dca8-111">`FindExportedTypeByName` Metoda používá standardní pravidla náhradník modul common language runtime k vyřešení odkazů.</span><span class="sxs-lookup"><span data-stu-id="8dca8-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dca8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8dca8-112">Requirements</span></span>  
 <span data-ttu-id="8dca8-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8dca8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8dca8-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8dca8-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8dca8-115">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8dca8-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="8dca8-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8dca8-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8dca8-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8dca8-117">See also</span></span>

- [<span data-ttu-id="8dca8-118">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8dca8-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="8dca8-119">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="8dca8-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
