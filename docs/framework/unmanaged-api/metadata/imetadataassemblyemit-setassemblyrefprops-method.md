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
ms.openlocfilehash: 5434aa2d12bd9a29a8c2fc784421442469ceb1ce
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440563"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="5b639-102">IMetaDataAssemblyEmit::SetAssemblyRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="5b639-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="5b639-103">Upraví zadanou `AssemblyRef` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="5b639-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b639-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b639-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="5b639-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b639-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="5b639-106">pro Token metadat, který určuje `AssemblyRef` strukturu metadat, která se má upravit.</span><span class="sxs-lookup"><span data-stu-id="5b639-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="5b639-107">pro Veřejný klíč vydavatele odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b639-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="5b639-108">pro Velikost v bajtech `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="5b639-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="5b639-109">pro Textový název sestavení čitelný lidmi</span><span class="sxs-lookup"><span data-stu-id="5b639-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="5b639-110">pro Ukazatel na instanci AssemblyMetadata –, která obsahuje informace o verzi, platformě a národním prostředí pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b639-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="5b639-111">pro Ukazatel na data algoritmu hash přidružená k sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b639-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="5b639-112">pro Velikost v bajtech `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="5b639-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="5b639-113">pro Bitová kombinace hodnot [AssemblyRefFlags –](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) , které určují atributy odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b639-113">[in] A bitwise combination of [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b639-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b639-114">Remarks</span></span>  
 <span data-ttu-id="5b639-115">Chcete-li vytvořit `AssemblyRef` struktury metadat, použijte metodu [IMetaDataAssemblyEmit::D efineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5b639-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b639-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b639-116">Requirements</span></span>  
 <span data-ttu-id="5b639-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b639-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b639-118">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5b639-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5b639-119">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="5b639-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5b639-120">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b639-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b639-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b639-121">See also</span></span>

- [<span data-ttu-id="5b639-122">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b639-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
