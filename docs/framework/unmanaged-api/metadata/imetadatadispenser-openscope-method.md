---
title: IMetaDataDispenser::OpenScope – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
ms.openlocfilehash: 5ce1af82631531f8f7105fbf92ba78db3cca437b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442325"
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="4c844-102">IMetaDataDispenser::OpenScope – metoda</span><span class="sxs-lookup"><span data-stu-id="4c844-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="4c844-103">Otevře existující soubor na disku a namapuje jeho metadata do paměti.</span><span class="sxs-lookup"><span data-stu-id="4c844-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c844-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c844-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c844-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c844-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="4c844-106">pro Název souboru, který se má otevřít</span><span class="sxs-lookup"><span data-stu-id="4c844-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="4c844-107">Soubor musí obsahovat metadata modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="4c844-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="4c844-108">pro Hodnota výčtu [CorOpenFlags –](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) , která určuje režim (čtení, zápis a tak dále) pro otevření.</span><span class="sxs-lookup"><span data-stu-id="4c844-108">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="4c844-109">pro Identifikátor IID požadovaného rozhraní metadat, které má být vráceno; Volající použije rozhraní k importu (čtení) nebo generování (zápisu) metadat.</span><span class="sxs-lookup"><span data-stu-id="4c844-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="4c844-110">Hodnota `riid` musí určovat jedno z rozhraní "Import" nebo "Emit".</span><span class="sxs-lookup"><span data-stu-id="4c844-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="4c844-111">Platné hodnoty jsou IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 nebo IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="4c844-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="4c844-112">mimo Ukazatel na vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4c844-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c844-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4c844-113">Remarks</span></span>  
 <span data-ttu-id="4c844-114">Kopie metadat v paměti se dá dotazovat pomocí metod z jednoho z rozhraní "Import" nebo přidat k použití metod z rozhraní typu "Emit".</span><span class="sxs-lookup"><span data-stu-id="4c844-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="4c844-115">Pokud cílový soubor neobsahuje metadata CLR, metoda `OpenScope` se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="4c844-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="4c844-116">Pokud je v .NET Framework verze 1,0 a verze 1,1, je v případě, že je obor otevřený s `dwOpenFlags` nastaveným na ofRead, nárok na sdílení.</span><span class="sxs-lookup"><span data-stu-id="4c844-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="4c844-117">To znamená, že pokud následná volání `OpenScope` přejdou na název souboru, který byl dříve otevřen, existující obor je znovu použit a nová sada datových struktur není vytvořena.</span><span class="sxs-lookup"><span data-stu-id="4c844-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="4c844-118">V důsledku tohoto sdílení ale může dojít k problémům.</span><span class="sxs-lookup"><span data-stu-id="4c844-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="4c844-119">V .NET Framework verze 2,0 se už nesdílí obory otevřené pomocí `dwOpenFlags` nastavené na ofRead.</span><span class="sxs-lookup"><span data-stu-id="4c844-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="4c844-120">K povolení sdílení oboru použijte hodnotu ofReadOnly.</span><span class="sxs-lookup"><span data-stu-id="4c844-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="4c844-121">Při sdílení oboru nebudou dotazy, které používají rozhraní metadat pro čtení a zápis, selžou.</span><span class="sxs-lookup"><span data-stu-id="4c844-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c844-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4c844-122">Requirements</span></span>  
 <span data-ttu-id="4c844-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c844-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c844-124">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4c844-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4c844-125">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="4c844-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4c844-126">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c844-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c844-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c844-127">See also</span></span>

- [<span data-ttu-id="4c844-128">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c844-128">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="4c844-129">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c844-129">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="4c844-130">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c844-130">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="4c844-131">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c844-131">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="4c844-132">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c844-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4c844-133">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c844-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="4c844-134">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c844-134">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4c844-135">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c844-135">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
