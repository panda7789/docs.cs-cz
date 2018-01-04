---
title: "IMetaDataAssemblyImport::EnumFiles – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.EnumFiles
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ce0682f6f7719c902183778578d75dd19d56867
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="b2b72-102">IMetaDataAssemblyImport::EnumFiles – metoda</span><span class="sxs-lookup"><span data-stu-id="b2b72-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="b2b72-103">Vytvoří výčet souborů v aktuální manifest sestavení odkazuje.</span><span class="sxs-lookup"><span data-stu-id="b2b72-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2b72-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2b72-104">Syntax</span></span>  
  
```  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,   
    [out] mdFile          rFiles[],   
    [in]  ULONG           cMax,   
    [out] ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2b72-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2b72-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b2b72-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="b2b72-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b2b72-107">Toto musí být pro první volání této metody hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b2b72-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="b2b72-108">[out] Pole používá k ukládání `mdFile` tokenů metadat.</span><span class="sxs-lookup"><span data-stu-id="b2b72-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b2b72-109">[v] Maximální počet `mdFile` tokeny, které mohou být umístěny v `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="b2b72-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="b2b72-110">[out] Počet `mdFile` tokeny umístěna v `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="b2b72-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2b72-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b2b72-111">Return Value</span></span>  
  
|<span data-ttu-id="b2b72-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2b72-112">HRESULT</span></span>|<span data-ttu-id="b2b72-113">Popis</span><span class="sxs-lookup"><span data-stu-id="b2b72-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b2b72-114">`EnumFiles`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="b2b72-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b2b72-115">Neexistují žádné tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="b2b72-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="b2b72-116">V takovém případě `pcTokens` je nastaven na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="b2b72-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2b72-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b2b72-117">Requirements</span></span>  
 <span data-ttu-id="b2b72-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2b72-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2b72-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b2b72-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2b72-120">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b2b72-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b2b72-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2b72-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2b72-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2b72-122">See Also</span></span>  
 [<span data-ttu-id="b2b72-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2b72-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
