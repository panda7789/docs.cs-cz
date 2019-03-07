---
title: IMetaDataAssemblyImport::EnumAssemblyRefs – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumAssemblyRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ba85ec920777189940a05864d19e4c24a65b4564
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499473"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="712c7-102">IMetaDataAssemblyImport::EnumAssemblyRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="712c7-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="712c7-103">Vytvoří výčet `mdAssemblyRef` instancí, které jsou definovány v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="712c7-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="712c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="712c7-104">Syntax</span></span>  
  
```  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="712c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="712c7-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="712c7-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="712c7-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="712c7-107">Musí se jednat s hodnotou null hodnotu v případě `EnumAssemblyRefs` je metoda volána poprvé.</span><span class="sxs-lookup"><span data-stu-id="712c7-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="712c7-108">[out] Výčet `mdAssemblyRef` tokeny metadat.</span><span class="sxs-lookup"><span data-stu-id="712c7-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="712c7-109">[in] Maximální počet tokenů, které je možné umístit `rAssemblyRefs` pole.</span><span class="sxs-lookup"><span data-stu-id="712c7-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="712c7-110">[out] Počet tokenů skutečně umístit v `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="712c7-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="712c7-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="712c7-111">Return Value</span></span>  
  
|<span data-ttu-id="712c7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="712c7-112">HRESULT</span></span>|<span data-ttu-id="712c7-113">Popis</span><span class="sxs-lookup"><span data-stu-id="712c7-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="712c7-114">`EnumAssemblyRefs` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="712c7-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="712c7-115">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="712c7-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="712c7-116">V takovém případě `pcTokens` je nastavena na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="712c7-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="712c7-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="712c7-117">Requirements</span></span>  
 <span data-ttu-id="712c7-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="712c7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="712c7-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="712c7-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="712c7-120">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="712c7-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="712c7-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="712c7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="712c7-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="712c7-122">See also</span></span>
- [<span data-ttu-id="712c7-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="712c7-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
