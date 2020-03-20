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
ms.openlocfilehash: cabd6a47e5d6fc2a4cea87b16d349d9c778b3507
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176055"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="c7369-102">IMetaDataAssemblyEmit::DefineFile – metoda</span><span class="sxs-lookup"><span data-stu-id="c7369-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="c7369-103">Vytvoří `File` strukturu metadat obsahující metadata pro sestavení odkazované tímto sestavením a vrátí přidružený token metadat.</span><span class="sxs-lookup"><span data-stu-id="c7369-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7369-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7369-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,
    [in]  const void     *pbHashValue,
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7369-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7369-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="c7369-106">[v] Název souboru, který má být spotřebován.</span><span class="sxs-lookup"><span data-stu-id="c7369-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="c7369-107">[v] Ukazatel na data hash přidružená k sestavení.</span><span class="sxs-lookup"><span data-stu-id="c7369-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="c7369-108">[v] Velikost v bajtů `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="c7369-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="c7369-109">[v] Bitová kombinace `FileFlags` hodnot, které určují nastavení vlastností.</span><span class="sxs-lookup"><span data-stu-id="c7369-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="c7369-110">[out] Ukazatel na vrácený `File` token.</span><span class="sxs-lookup"><span data-stu-id="c7369-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7369-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c7369-111">Remarks</span></span>  
 <span data-ttu-id="c7369-112">Pro `File` každý soubor, který byl součástí tohoto sestavení v době sestavení tohoto sestavení, musí být definována jedna struktura metadat, s výjimkou souboru, který obsahuje metadata.</span><span class="sxs-lookup"><span data-stu-id="c7369-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7369-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7369-113">Requirements</span></span>  
 <span data-ttu-id="c7369-114">**Platforma:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7369-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7369-115">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="c7369-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c7369-116">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c7369-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c7369-117">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7369-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7369-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7369-118">See also</span></span>

- [<span data-ttu-id="c7369-119">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c7369-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
