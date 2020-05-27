---
title: IMetaDataAssemblyEmit::SetAssemblyRefProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type:
- apiref
ms.openlocfilehash: fb381a872cbeb787da0c6920f2cdeef434fb33ea
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008089"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="a4c2e-102">IMetaDataAssemblyEmit::SetAssemblyRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="a4c2e-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="a4c2e-103">Upraví zadanou `AssemblyRef` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="a4c2e-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4c2e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4c2e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyRefProps (  
    [in] mdAssemblyRef              ar,  
    [in] const void                 *pbPublicKeyOrToken,  
    [in] ULONG                      cbPublicKeyOrToken,  
    [in] LPCWSTR                    szName,
    [in] const ASSEMBLYMETADATA     *pMetaData,
    [in] const void                 *pbHashValue,  
    [in] ULONG                      cbHashValue,  
    [in] DWORD                      dwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4c2e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4c2e-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="a4c2e-106">pro Token metadat, který určuje `AssemblyRef` strukturu metadat, která má být upravena.</span><span class="sxs-lookup"><span data-stu-id="a4c2e-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="a4c2e-107">pro Veřejný klíč vydavatele odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="a4c2e-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="a4c2e-108">pro Velikost v bajtech `pbPublicKeyOrToken` .</span><span class="sxs-lookup"><span data-stu-id="a4c2e-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="a4c2e-109">pro Textový název sestavení čitelný lidmi</span><span class="sxs-lookup"><span data-stu-id="a4c2e-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="a4c2e-110">pro Ukazatel na instanci AssemblyMetadata –, která obsahuje informace o verzi, platformě a národním prostředí pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="a4c2e-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="a4c2e-111">pro Ukazatel na data algoritmu hash přidružená k sestavení.</span><span class="sxs-lookup"><span data-stu-id="a4c2e-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="a4c2e-112">pro Velikost v bajtech `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="a4c2e-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="a4c2e-113">pro Bitová kombinace hodnot [AssemblyRefFlags –](assemblyrefflags-enumeration.md) , které určují atributy odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="a4c2e-113">[in] A bitwise combination of [AssemblyRefFlags](assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4c2e-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4c2e-114">Remarks</span></span>  
 <span data-ttu-id="a4c2e-115">Chcete-li vytvořit `AssemblyRef` strukturu metadat, použijte metodu [IMetaDataAssemblyEmit::D efineassemblyref](imetadataassemblyemit-defineassemblyref-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a4c2e-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4c2e-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a4c2e-116">Requirements</span></span>  
 <span data-ttu-id="a4c2e-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4c2e-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4c2e-118">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a4c2e-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a4c2e-119">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="a4c2e-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a4c2e-120">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4c2e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c2e-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4c2e-121">See also</span></span>

- [<span data-ttu-id="a4c2e-122">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a4c2e-122">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
