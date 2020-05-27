---
title: IMetaDataDispenser::OpenScopeOnMemory – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScopeOnMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type:
- apiref
ms.openlocfilehash: 69e5e05012d2b44a76a986591ec990f66bf8ae20
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007322"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="b4250-102">IMetaDataDispenser::OpenScopeOnMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="b4250-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="b4250-103">Otevře oblast paměti, která obsahuje existující metadata.</span><span class="sxs-lookup"><span data-stu-id="b4250-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="b4250-104">To znamená, že tato metoda otevře zadanou oblast paměti, ve které jsou stávající data považována za metadata.</span><span class="sxs-lookup"><span data-stu-id="b4250-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4250-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4250-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,
    [in]  ULONG       cbData,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4250-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4250-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="b4250-107">pro Ukazatel, který určuje počáteční adresu oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="b4250-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="b4250-108">pro Velikost oblasti paměti (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="b4250-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="b4250-109">pro Hodnota výčtu [CorOpenFlags –](coropenflags-enumeration.md) , která určuje režim (čtení, zápis a tak dále) pro otevření.</span><span class="sxs-lookup"><span data-stu-id="b4250-109">[in] A value of the [CorOpenFlags](coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="b4250-110">pro Identifikátor IID požadovaného rozhraní metadat, které má být vráceno; Volající použije rozhraní k importu (čtení) nebo generování (zápisu) metadat.</span><span class="sxs-lookup"><span data-stu-id="b4250-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="b4250-111">Hodnota `riid` musí určovat jedno z rozhraní "Import" nebo "Emit".</span><span class="sxs-lookup"><span data-stu-id="b4250-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="b4250-112">Platné hodnoty jsou IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 nebo IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="b4250-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="b4250-113">mimo Ukazatel na vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b4250-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4250-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4250-114">Remarks</span></span>  
 <span data-ttu-id="b4250-115">Kopie metadat v paměti se dá dotazovat pomocí metod z jednoho z rozhraní "Import" nebo přidat k použití metod z rozhraní typu "Emit".</span><span class="sxs-lookup"><span data-stu-id="b4250-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="b4250-116">`OpenScopeOnMemory`Metoda je podobná metodě [IMetaDataDispenser:: OpenScope –](imetadatadispenser-openscope-method.md) s tím rozdílem, že metadata zájmu již existují v paměti, nikoli v souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="b4250-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="b4250-117">Pokud cílová oblast paměti neobsahuje metadata modulu CLR (Common Language Runtime), `OpenScopeOnMemory` metoda se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="b4250-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4250-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4250-118">Requirements</span></span>  
 <span data-ttu-id="b4250-119">**Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4250-119">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4250-120">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b4250-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b4250-121">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="b4250-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b4250-122">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4250-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4250-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4250-123">See also</span></span>

- [<span data-ttu-id="b4250-124">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4250-124">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="b4250-125">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4250-125">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="b4250-126">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4250-126">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="b4250-127">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4250-127">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="b4250-128">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4250-128">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="b4250-129">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4250-129">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="b4250-130">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4250-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b4250-131">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4250-131">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
