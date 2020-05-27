---
title: IMetaDataAssemblyEmit::DefineAssembly – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
ms.openlocfilehash: 17c91200730431c4c6e230b8c1561ce7c4863868
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008180"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="1490d-102">IMetaDataAssemblyEmit::DefineAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="1490d-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="1490d-103">Vytvoří `Assembly` strukturu obsahující metadata pro zadané sestavení a vrátí přidružený token metadat.</span><span class="sxs-lookup"><span data-stu-id="1490d-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1490d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1490d-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1490d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1490d-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="1490d-106">pro Veřejný klíč, který identifikuje vydavatele sestavení, nebo hodnotu NULL, pokud sestavení není silně pojmenováno.</span><span class="sxs-lookup"><span data-stu-id="1490d-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="1490d-107">pro Velikost v bajtech `pbPublicKey` .</span><span class="sxs-lookup"><span data-stu-id="1490d-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="1490d-108">pro Identifikátor algoritmu hash, který má být použit k zašifrování souborů v sestavení, nebo hodnota NULL pro určení algoritmu SHA-1.</span><span class="sxs-lookup"><span data-stu-id="1490d-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="1490d-109">pro Textový název sestavení čitelný lidmi</span><span class="sxs-lookup"><span data-stu-id="1490d-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="1490d-110">Tato hodnota nesmí překročit 1024 znaků.</span><span class="sxs-lookup"><span data-stu-id="1490d-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="1490d-111">pro Ukazatel na instanci AssemblyMetadata –, která obsahuje informace o verzi, platformě a národním prostředí pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="1490d-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="1490d-112">pro Kombinace hodnot [CorAssemblyFlags –](corassemblyflags-enumeration.md) popisujících funkce sestavení.</span><span class="sxs-lookup"><span data-stu-id="1490d-112">[in] A combination of [CorAssemblyFlags](corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="1490d-113">mimo Ukazatel na token metadat.</span><span class="sxs-lookup"><span data-stu-id="1490d-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1490d-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1490d-114">Remarks</span></span>  
 <span data-ttu-id="1490d-115">`Assembly`V rámci manifestu lze definovat pouze jednu strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="1490d-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1490d-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1490d-116">Requirements</span></span>  
 <span data-ttu-id="1490d-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1490d-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1490d-118">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1490d-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1490d-119">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1490d-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1490d-120">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1490d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1490d-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="1490d-121">See also</span></span>

- [<span data-ttu-id="1490d-122">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1490d-122">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
