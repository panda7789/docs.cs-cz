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
ms.openlocfilehash: 8d9de753f1c44338a96e990def80643d591f2a8b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007465"
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="b7e46-102">IMetaDataDispenser::OpenScope – metoda</span><span class="sxs-lookup"><span data-stu-id="b7e46-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="b7e46-103">Otevře existující soubor na disku a namapuje jeho metadata do paměti.</span><span class="sxs-lookup"><span data-stu-id="b7e46-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7e46-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7e46-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7e46-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7e46-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="b7e46-106">pro Název souboru, který se má otevřít</span><span class="sxs-lookup"><span data-stu-id="b7e46-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="b7e46-107">Soubor musí obsahovat metadata modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="b7e46-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="b7e46-108">pro Hodnota výčtu [CorOpenFlags –](coropenflags-enumeration.md) , která určuje režim (čtení, zápis a tak dále) pro otevření.</span><span class="sxs-lookup"><span data-stu-id="b7e46-108">[in] A value of the [CorOpenFlags](coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="b7e46-109">pro Identifikátor IID požadovaného rozhraní metadat, které má být vráceno; Volající použije rozhraní k importu (čtení) nebo generování (zápisu) metadat.</span><span class="sxs-lookup"><span data-stu-id="b7e46-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="b7e46-110">Hodnota `riid` musí určovat jedno z rozhraní "Import" nebo "Emit".</span><span class="sxs-lookup"><span data-stu-id="b7e46-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="b7e46-111">Platné hodnoty jsou IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 nebo IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="b7e46-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="b7e46-112">mimo Ukazatel na vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b7e46-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7e46-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7e46-113">Remarks</span></span>  
 <span data-ttu-id="b7e46-114">Kopie metadat v paměti se dá dotazovat pomocí metod z jednoho z rozhraní "Import" nebo přidat k použití metod z rozhraní typu "Emit".</span><span class="sxs-lookup"><span data-stu-id="b7e46-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="b7e46-115">Pokud cílový soubor neobsahuje metadata CLR, `OpenScope` metoda se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="b7e46-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="b7e46-116">Pokud je v .NET Framework verze 1,0 a verze 1,1, je v případě otevření oboru s `dwOpenFlags` nastavením na ofRead nárok na sdílení.</span><span class="sxs-lookup"><span data-stu-id="b7e46-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="b7e46-117">To znamená, že pokud následná volání `OpenScope` přejdoucí na název souboru, který byl dříve otevřen, existující obor je znovu použit a nová sada datových struktur není vytvořena.</span><span class="sxs-lookup"><span data-stu-id="b7e46-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="b7e46-118">V důsledku tohoto sdílení ale může dojít k problémům.</span><span class="sxs-lookup"><span data-stu-id="b7e46-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="b7e46-119">V .NET Framework verze 2,0 již nejsou obory otevřené s `dwOpenFlags` nastavenou na ofRead nadále sdíleny.</span><span class="sxs-lookup"><span data-stu-id="b7e46-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="b7e46-120">K povolení sdílení oboru použijte hodnotu ofReadOnly.</span><span class="sxs-lookup"><span data-stu-id="b7e46-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="b7e46-121">Při sdílení oboru nebudou dotazy, které používají rozhraní metadat pro čtení a zápis, selžou.</span><span class="sxs-lookup"><span data-stu-id="b7e46-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7e46-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7e46-122">Requirements</span></span>  
 <span data-ttu-id="b7e46-123">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7e46-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7e46-124">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b7e46-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b7e46-125">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="b7e46-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b7e46-126">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7e46-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7e46-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7e46-127">See also</span></span>

- [<span data-ttu-id="b7e46-128">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7e46-128">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="b7e46-129">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7e46-129">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="b7e46-130">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7e46-130">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="b7e46-131">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7e46-131">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="b7e46-132">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7e46-132">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="b7e46-133">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7e46-133">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="b7e46-134">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7e46-134">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b7e46-135">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7e46-135">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
