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
ms.openlocfilehash: 61d81c94e3a9c092b5d45791962635c761e8da8a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008141"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="ea187-102">IMetaDataAssemblyEmit::DefineFile – metoda</span><span class="sxs-lookup"><span data-stu-id="ea187-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="ea187-103">Vytvoří `File` strukturu metadat obsahující metadata pro sestavení, na které odkazuje toto sestavení, a vrátí přidružený token metadat.</span><span class="sxs-lookup"><span data-stu-id="ea187-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea187-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea187-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,
    [in]  const void     *pbHashValue,
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea187-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea187-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="ea187-106">pro Název souboru, který se má spotřebovat</span><span class="sxs-lookup"><span data-stu-id="ea187-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="ea187-107">pro Ukazatel na data algoritmu hash přidružená k sestavení.</span><span class="sxs-lookup"><span data-stu-id="ea187-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="ea187-108">pro Velikost v bajtech `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="ea187-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="ea187-109">pro Bitová kombinace `FileFlags` hodnot, které určují nastavení vlastností.</span><span class="sxs-lookup"><span data-stu-id="ea187-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="ea187-110">mimo Ukazatel na vrácený `File` token.</span><span class="sxs-lookup"><span data-stu-id="ea187-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea187-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ea187-111">Remarks</span></span>  
 <span data-ttu-id="ea187-112">`File`Pro každý soubor, který byl součástí tohoto sestavení v době, kdy bylo sestavení sestaveno, musí být definována jedna struktura metadat s výjimkou souboru, který obsahuje metadata.</span><span class="sxs-lookup"><span data-stu-id="ea187-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea187-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea187-113">Requirements</span></span>  
 <span data-ttu-id="ea187-114">**Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea187-114">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea187-115">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ea187-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ea187-116">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="ea187-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ea187-117">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea187-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea187-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea187-118">See also</span></span>

- [<span data-ttu-id="ea187-119">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea187-119">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
