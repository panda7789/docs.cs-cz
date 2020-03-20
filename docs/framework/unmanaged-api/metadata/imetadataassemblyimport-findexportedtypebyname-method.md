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
ms.openlocfilehash: edfe5de9c9d7ef9607a2eea5146194bbd4393a92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175990"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="57bea-102">IMetaDataAssemblyImport::FindExportedTypeByName – metoda</span><span class="sxs-lookup"><span data-stu-id="57bea-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="57bea-103">Získá ukazatel exportovaného typu, vzhledem k jeho názvu a ohraničující ho.</span><span class="sxs-lookup"><span data-stu-id="57bea-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57bea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57bea-104">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,
    [in]  mdToken           mdtExportedType,
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57bea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57bea-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="57bea-106">[v] Název exportovaného typu.</span><span class="sxs-lookup"><span data-stu-id="57bea-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="57bea-107">[v] Token metadat pro ohraničující třídu exportovaného typu.</span><span class="sxs-lookup"><span data-stu-id="57bea-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="57bea-108">Tato hodnota `mdExportedTypeNil` je, pokud požadovaný exportovaný typ není vnořený typ.</span><span class="sxs-lookup"><span data-stu-id="57bea-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="57bea-109">[out] Ukazatel na `mdExportedType` token, který představuje exportovaný typ.</span><span class="sxs-lookup"><span data-stu-id="57bea-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57bea-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57bea-110">Remarks</span></span>  
 <span data-ttu-id="57bea-111">Metoda `FindExportedTypeByName` používá standardní pravidla používaná za běhu společného jazyka pro řešení odkazů.</span><span class="sxs-lookup"><span data-stu-id="57bea-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57bea-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57bea-112">Requirements</span></span>  
 <span data-ttu-id="57bea-113">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57bea-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57bea-114">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="57bea-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="57bea-115">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="57bea-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="57bea-116">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57bea-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57bea-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="57bea-117">See also</span></span>

- [<span data-ttu-id="57bea-118">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57bea-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="57bea-119">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="57bea-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
