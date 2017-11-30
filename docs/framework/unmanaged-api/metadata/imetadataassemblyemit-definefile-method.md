---
title: "IMetaDataAssemblyEmit::DefineFile – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineFile
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f3be44603eb16c6e74b34c0f569fc5bb11264ca0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="e6e3b-102">IMetaDataAssemblyEmit::DefineFile – metoda</span><span class="sxs-lookup"><span data-stu-id="e6e3b-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="e6e3b-103">Vytvoří `File` strukturu metadat obsahující metadata pro sestavení odkazuje toto sestavení a vrátí token přidružených metadat.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6e3b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6e3b-104">Syntax</span></span>  
  
```  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6e3b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e6e3b-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="e6e3b-106">[v] Název souboru, který se má používat.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="e6e3b-107">[v] Ukazatel na hodnotu hash data přidružená k sestavení.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="e6e3b-108">[v] Velikost v bajtech `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="e6e3b-109">[v] Bitové kombinace `FileFlags` hodnoty, které určují nastavení vlastností.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="e6e3b-110">[out] Ukazatel na vrácený `File` tokenu.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6e3b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6e3b-111">Remarks</span></span>  
 <span data-ttu-id="e6e3b-112">Jeden `File` strukturu metadat musí být definovaná pro každý soubor, který byl součástí toto sestavení v čase, který byl vytvořený toto sestavení, s výjimkou souboru, který obsahuje metadata.</span><span class="sxs-lookup"><span data-stu-id="e6e3b-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6e3b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6e3b-113">Requirements</span></span>  
 <span data-ttu-id="e6e3b-114">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6e3b-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6e3b-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e6e3b-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e6e3b-116">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e6e3b-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e6e3b-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6e3b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6e3b-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6e3b-118">See Also</span></span>  
 [<span data-ttu-id="e6e3b-119">Imetadataassemblyemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e6e3b-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
