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
ms.openlocfilehash: 048c7234fcb2592ea0dade135a32341a6e0f404f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444916"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="f3e94-102">IMetaDataAssemblyImport::FindExportedTypeByName – metoda</span><span class="sxs-lookup"><span data-stu-id="f3e94-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="f3e94-103">Získá ukazatel na typ exportovaný daného názvu a nadřazený typ.</span><span class="sxs-lookup"><span data-stu-id="f3e94-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3e94-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3e94-104">Syntax</span></span>  
  
```  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3e94-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3e94-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="f3e94-106">[v] Název typu exportovaný.</span><span class="sxs-lookup"><span data-stu-id="f3e94-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="f3e94-107">[v] Token metadat pro třídu nadřazených exportovaný typu.</span><span class="sxs-lookup"><span data-stu-id="f3e94-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="f3e94-108">Tato hodnota je `mdExportedTypeNil` Pokud požadované exportovaný typ není typu vnořené.</span><span class="sxs-lookup"><span data-stu-id="f3e94-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="f3e94-109">[out] Ukazatel `mdExportedType` token, který představuje typ exportovaný.</span><span class="sxs-lookup"><span data-stu-id="f3e94-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3e94-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3e94-110">Remarks</span></span>  
 <span data-ttu-id="f3e94-111">`FindExportedTypeByName` Metoda používá standardní pravidla zaměstnaní modul common language runtime pro řešení odkazů.</span><span class="sxs-lookup"><span data-stu-id="f3e94-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3e94-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3e94-112">Requirements</span></span>  
 <span data-ttu-id="f3e94-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3e94-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3e94-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f3e94-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3e94-115">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f3e94-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3e94-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3e94-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3e94-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3e94-117">See Also</span></span>  
 [<span data-ttu-id="f3e94-118">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3e94-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="f3e94-119">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="f3e94-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
