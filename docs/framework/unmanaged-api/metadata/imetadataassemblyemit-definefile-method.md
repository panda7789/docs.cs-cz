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
ms.openlocfilehash: 0b7ca6f9878ed2fa2d90ea93e5101f0a66ec2d5e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440203"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="3f4a3-102">IMetaDataAssemblyEmit::DefineFile – metoda</span><span class="sxs-lookup"><span data-stu-id="3f4a3-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="3f4a3-103">Vytvoří `File` strukturu metadat obsahující metadata pro sestavení, na které odkazuje toto sestavení, a vrátí přidružený token metadat.</span><span class="sxs-lookup"><span data-stu-id="3f4a3-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f4a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f4a3-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f4a3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f4a3-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="3f4a3-106">pro Název souboru, který se má spotřebovat</span><span class="sxs-lookup"><span data-stu-id="3f4a3-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="3f4a3-107">pro Ukazatel na data algoritmu hash přidružená k sestavení.</span><span class="sxs-lookup"><span data-stu-id="3f4a3-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="3f4a3-108">pro Velikost v bajtech `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="3f4a3-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="3f4a3-109">pro Bitová kombinace hodnot `FileFlags`, které určují nastavení vlastností.</span><span class="sxs-lookup"><span data-stu-id="3f4a3-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="3f4a3-110">mimo Ukazatel na vrácený token `File`.</span><span class="sxs-lookup"><span data-stu-id="3f4a3-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f4a3-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3f4a3-111">Remarks</span></span>  
 <span data-ttu-id="3f4a3-112">Pro každý soubor, který byl součástí tohoto sestavení v době, kdy bylo sestavení sestaveno, je třeba definovat jednu `File` strukturu metadat, a to s výjimkou souboru, který obsahuje metadata.</span><span class="sxs-lookup"><span data-stu-id="3f4a3-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f4a3-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3f4a3-113">Requirements</span></span>  
 <span data-ttu-id="3f4a3-114">**Platforma:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f4a3-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f4a3-115">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3f4a3-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f4a3-116">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="3f4a3-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f4a3-117">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f4a3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f4a3-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f4a3-118">See also</span></span>

- [<span data-ttu-id="3f4a3-119">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3f4a3-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
