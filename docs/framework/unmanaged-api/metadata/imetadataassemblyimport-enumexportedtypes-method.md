---
title: "IMetaDataAssemblyImport::EnumExportedTypes – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.EnumExportedTypes
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54b5a51dc0a12bb4c159b61252c9db0a82f03518
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="63bf2-102">IMetaDataAssemblyImport::EnumExportedTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="63bf2-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="63bf2-103">Vytvoří výčet odkazovaných v manifestu sestavení v aktuálním oboru metadata exportovaný typů.</span><span class="sxs-lookup"><span data-stu-id="63bf2-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63bf2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63bf2-104">Syntax</span></span>  
  
```  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,   
    [out] mdExportedType   rExportedTypes[],   
    [in]  ULONG            cMax,   
    [out] ULONG            *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="63bf2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="63bf2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="63bf2-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="63bf2-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="63bf2-107">Tato hodnota musí být null hodnotu v případě `EnumExportedTypes` metoda je volána poprvé.</span><span class="sxs-lookup"><span data-stu-id="63bf2-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="63bf2-108">[out] Výčet `mdExportedType` tokenů metadat.</span><span class="sxs-lookup"><span data-stu-id="63bf2-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="63bf2-109">[v] Maximální počet `mdExportedType` tokeny, které může být umístěno `rExportedTypes` pole.</span><span class="sxs-lookup"><span data-stu-id="63bf2-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="63bf2-110">[out] Počet `mdExportedType` tokeny umístěna v `rExportedTypes`.</span><span class="sxs-lookup"><span data-stu-id="63bf2-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63bf2-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="63bf2-111">Return Value</span></span>  
  
|<span data-ttu-id="63bf2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="63bf2-112">HRESULT</span></span>|<span data-ttu-id="63bf2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="63bf2-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="63bf2-114">`EnumExportedTypes`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="63bf2-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="63bf2-115">Neexistují žádné tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="63bf2-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="63bf2-116">V takovém případě `pcTokens` je nastaven na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="63bf2-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63bf2-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63bf2-117">Requirements</span></span>  
 <span data-ttu-id="63bf2-118">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63bf2-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63bf2-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="63bf2-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="63bf2-120">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="63bf2-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="63bf2-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63bf2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63bf2-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="63bf2-122">See Also</span></span>  
 [<span data-ttu-id="63bf2-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63bf2-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
