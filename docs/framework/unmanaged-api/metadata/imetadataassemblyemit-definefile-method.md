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
ms.openlocfilehash: 5ede66a39de292cd259cb12742e7c6df4ab5814f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720493"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="0ed87-102">IMetaDataAssemblyEmit::DefineFile – metoda</span><span class="sxs-lookup"><span data-stu-id="0ed87-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="0ed87-103">Vytvoří `File` struktury metadat obsahující metadata pro sestavení odkazuje toto sestavení a vrátí token metadat.</span><span class="sxs-lookup"><span data-stu-id="0ed87-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ed87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ed87-104">Syntax</span></span>  
  
```  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ed87-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ed87-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="0ed87-106">[in] Název souboru, který se má používat.</span><span class="sxs-lookup"><span data-stu-id="0ed87-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="0ed87-107">[in] Ukazatel na hodnotu hash dat přidružené k sestavení.</span><span class="sxs-lookup"><span data-stu-id="0ed87-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="0ed87-108">[in] Velikost v bajtech `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="0ed87-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="0ed87-109">[in] Bitová kombinace hodnot `FileFlags` hodnoty, které určují nastavení vlastností.</span><span class="sxs-lookup"><span data-stu-id="0ed87-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="0ed87-110">[out] Ukazatel na vrácenou `File` token.</span><span class="sxs-lookup"><span data-stu-id="0ed87-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ed87-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ed87-111">Remarks</span></span>  
 <span data-ttu-id="0ed87-112">Jeden `File` struktury metadat musí být definované pro každý soubor, který byl součástí tohoto sestavení v době, toto sestavení bylo sestaveno, s výjimkou souboru, který obsahuje metadata.</span><span class="sxs-lookup"><span data-stu-id="0ed87-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ed87-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ed87-113">Requirements</span></span>  
 <span data-ttu-id="0ed87-114">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ed87-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ed87-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0ed87-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0ed87-116">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0ed87-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0ed87-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ed87-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ed87-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ed87-118">See also</span></span>
- [<span data-ttu-id="0ed87-119">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ed87-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
