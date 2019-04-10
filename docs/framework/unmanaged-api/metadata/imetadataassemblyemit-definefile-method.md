---
title: IMetaDataAssemblyEmit::DefineFile – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5693da3b5e6d883efd9ad8a5a409a5dba8dd8b6e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203428"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="f541b-102">IMetaDataAssemblyEmit::DefineFile – metoda</span><span class="sxs-lookup"><span data-stu-id="f541b-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="f541b-103">Vytvoří `File` struktury metadat obsahující metadata pro sestavení odkazuje toto sestavení a vrátí token metadat.</span><span class="sxs-lookup"><span data-stu-id="f541b-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f541b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f541b-104">Syntax</span></span>  
  
```  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f541b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f541b-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="f541b-106">[in] Název souboru, který se má používat.</span><span class="sxs-lookup"><span data-stu-id="f541b-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="f541b-107">[in] Ukazatel na hodnotu hash dat přidružené k sestavení.</span><span class="sxs-lookup"><span data-stu-id="f541b-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="f541b-108">[in] Velikost v bajtech `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="f541b-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="f541b-109">[in] Bitová kombinace hodnot `FileFlags` hodnoty, které určují nastavení vlastností.</span><span class="sxs-lookup"><span data-stu-id="f541b-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="f541b-110">[out] Ukazatel na vrácenou `File` token.</span><span class="sxs-lookup"><span data-stu-id="f541b-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f541b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f541b-111">Remarks</span></span>  
 <span data-ttu-id="f541b-112">Jeden `File` struktury metadat musí být definované pro každý soubor, který byl součástí tohoto sestavení v době, toto sestavení bylo sestaveno, s výjimkou souboru, který obsahuje metadata.</span><span class="sxs-lookup"><span data-stu-id="f541b-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f541b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f541b-113">Requirements</span></span>  
 <span data-ttu-id="f541b-114">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f541b-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f541b-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f541b-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f541b-116">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f541b-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="f541b-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f541b-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f541b-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f541b-118">See also</span></span>

- [<span data-ttu-id="f541b-119">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f541b-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
