---
title: "IMetaDataAssemblyImport::FindExportedTypeByName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.FindExportedTypeByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::FindExportedTypeByName
helpviewer_keywords:
- FindExportedTypeByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindExportedTypeByName method [.NET Framework metadata]
ms.assetid: 46264b2c-574d-4dde-aafc-77187a104fdd
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b7ef0e09cb5a44e612e545fc4ee7278c2d128174
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="d50d4-102">IMetaDataAssemblyImport::FindExportedTypeByName – metoda</span><span class="sxs-lookup"><span data-stu-id="d50d4-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="d50d4-103">Získá ukazatel na typ exportovaný daného názvu a nadřazený typ.</span><span class="sxs-lookup"><span data-stu-id="d50d4-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d50d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d50d4-104">Syntax</span></span>  
  
```  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d50d4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d50d4-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="d50d4-106">[v] Název typu exportovaný.</span><span class="sxs-lookup"><span data-stu-id="d50d4-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="d50d4-107">[v] Token metadat pro třídu nadřazených exportovaný typu.</span><span class="sxs-lookup"><span data-stu-id="d50d4-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="d50d4-108">Tato hodnota je `mdExportedTypeNil` Pokud požadované exportovaný typ není typu vnořené.</span><span class="sxs-lookup"><span data-stu-id="d50d4-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="d50d4-109">[out] Ukazatel `mdExportedType` token, který představuje typ exportovaný.</span><span class="sxs-lookup"><span data-stu-id="d50d4-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d50d4-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d50d4-110">Remarks</span></span>  
 <span data-ttu-id="d50d4-111">`FindExportedTypeByName` Metoda používá standardní pravidla zaměstnaní modul common language runtime pro řešení odkazů.</span><span class="sxs-lookup"><span data-stu-id="d50d4-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d50d4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d50d4-112">Requirements</span></span>  
 <span data-ttu-id="d50d4-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d50d4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d50d4-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d50d4-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d50d4-115">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d50d4-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d50d4-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d50d4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d50d4-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d50d4-117">See Also</span></span>  
 [<span data-ttu-id="d50d4-118">Imetadataassemblyimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d50d4-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="d50d4-119">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="d50d4-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
