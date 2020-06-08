---
title: IMetaDataDispenser::DefineScope – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.DefineScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type:
- apiref
ms.openlocfilehash: 12a32b5d2f0647ea2d9b696d08d6644e30be0c65
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501349"
---
# <a name="imetadatadispenserdefinescope-method"></a><span data-ttu-id="4a882-102">IMetaDataDispenser::DefineScope – metoda</span><span class="sxs-lookup"><span data-stu-id="4a882-102">IMetaDataDispenser::DefineScope Method</span></span>
<span data-ttu-id="4a882-103">Vytvoří novou oblast v paměti, ve které můžete vytvořit nová metadata.</span><span class="sxs-lookup"><span data-stu-id="4a882-103">Creates a new area in memory in which you can create new metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a882-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a882-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a882-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a882-105">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="4a882-106">pro Identifikátor CLSID verze struktur metadat, které se mají vytvořit.</span><span class="sxs-lookup"><span data-stu-id="4a882-106">[in] The CLSID of the version of metadata structures to be created.</span></span> <span data-ttu-id="4a882-107">Tato hodnota musí být CLSID_CorMetaDataRuntime pro .NET Framework verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="4a882-107">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span></span>  
  
 `dwCreateFlags`  
 <span data-ttu-id="4a882-108">pro Příznaky, které určují možnosti.</span><span class="sxs-lookup"><span data-stu-id="4a882-108">[in] Flags that specify options.</span></span> <span data-ttu-id="4a882-109">Tato hodnota musí být nula pro .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="4a882-109">This value must be zero for the .NET Framework 2.0.</span></span>  
  
 `riid`  
 <span data-ttu-id="4a882-110">pro Identifikátor IID požadovaného rozhraní metadat, které má být vráceno; Volající použije rozhraní k vytvoření nových metadat.</span><span class="sxs-lookup"><span data-stu-id="4a882-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span></span>  
  
 <span data-ttu-id="4a882-111">Hodnota `riid` musí určovat jedno z rozhraní Emit.</span><span class="sxs-lookup"><span data-stu-id="4a882-111">The value of `riid` must specify one of the "emit" interfaces.</span></span> <span data-ttu-id="4a882-112">Platné hodnoty jsou IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit nebo IID_IMetaDataEmit2.</span><span class="sxs-lookup"><span data-stu-id="4a882-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="4a882-113">mimo Ukazatel na vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4a882-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a882-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a882-114">Remarks</span></span>  
 <span data-ttu-id="4a882-115">`DefineScope`Vytvoří sadu tabulek metadat v paměti, vygeneruje jedinečný identifikátor GUID (identifikátor verze modulu nebo identifikátor MVID) pro metadata a vytvoří položku v tabulce modulů pro vygenerování kompilační jednotky.</span><span class="sxs-lookup"><span data-stu-id="4a882-115">`DefineScope` creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span></span>  
  
 <span data-ttu-id="4a882-116">Atributy můžete k oboru metadat připojit jako celek pomocí metody [IMetaDataEmit:: SetModuleProps –](imetadataemit-setmoduleprops-method.md) nebo [IMetaDataEmit::D efinecustomattribute](imetadataemit-definecustomattribute-method.md) , podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="4a882-116">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](imetadataemit-definecustomattribute-method.md) method, as appropriate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a882-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4a882-117">Requirements</span></span>  
 <span data-ttu-id="4a882-118">**Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a882-118">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a882-119">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4a882-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4a882-120">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="4a882-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4a882-121">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a882-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a882-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a882-122">See also</span></span>

- [<span data-ttu-id="4a882-123">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a882-123">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="4a882-124">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a882-124">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="4a882-125">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a882-125">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="4a882-126">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a882-126">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="4a882-127">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a882-127">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
