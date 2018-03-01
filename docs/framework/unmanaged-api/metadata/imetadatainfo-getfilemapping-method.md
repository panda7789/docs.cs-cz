---
title: "IMetaDataInfo::GetFileMapping – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataInfo.GetFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f974230dc5ddf2a663f05fc06850f49f1de6e773
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="6ac9c-102">IMetaDataInfo::GetFileMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="6ac9c-102">IMetaDataInfo::GetFileMapping Method</span></span>
<span data-ttu-id="6ac9c-103">Získá oblasti paměti mapovaný soubor, a typ mapování.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ac9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ac9c-104">Syntax</span></span>  
  
```  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ac9c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ac9c-105">Parameters</span></span>  
 `ppvData`  
 <span data-ttu-id="6ac9c-106">[out] Ukazatel na začátek mapovaný soubor.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="6ac9c-107">[out] Velikost oblasti namapované.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="6ac9c-108">Pokud `pdwMappingType` je `fmFlat`, toto je velikost souboru.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="6ac9c-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) hodnotu, která určuje typ mapování.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="6ac9c-110">Vrátí aktuální implementace common language runtime (CLR) vždy `fmFlat`.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="6ac9c-111">Ostatní hodnoty jsou vyhrazené pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-111">Other values are reserved for future use.</span></span> <span data-ttu-id="6ac9c-112">Však vždy ověřte vrácené hodnoty, protože jiné hodnoty může v budoucích verzích povolené nebo služby verzích.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ac9c-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6ac9c-113">Return Value</span></span>  
  
|<span data-ttu-id="6ac9c-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6ac9c-114">HRESULT</span></span>|<span data-ttu-id="6ac9c-115">Popis</span><span class="sxs-lookup"><span data-stu-id="6ac9c-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6ac9c-116">Všechny výstupy jsou vyplněny.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="6ac9c-117">Jako hodnota argumentu byla předána hodnota NULL.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="6ac9c-118">Implementace CLR nemůže poskytnout informace o oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="6ac9c-119">Toto může nastat z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="6ac9c-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="6ac9c-120">-Oboru metadata byla otevřena s `ofWrite` nebo `ofCopyMemory` příznak.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="6ac9c-121">-Oboru metadata byla otevřena bez `ofReadOnly` příznak.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="6ac9c-122">-Na [imetadatadispenser::openscopeonmemory –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) metoda použitý k otevření pouze metadata část souboru.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="6ac9c-123">-Soubor není souborem přenosné spustitelný soubor (PE).</span><span class="sxs-lookup"><span data-stu-id="6ac9c-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="6ac9c-124">**Poznámka:** tyto podmínky závisí na implementaci CLR a jsou nejspíš oslabí v budoucích verzích modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ac9c-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ac9c-125">Remarks</span></span>  
 <span data-ttu-id="6ac9c-126">Paměť, `ppvData` body, je platný pouze základní obor metadat je otevřený.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="6ac9c-127">V pořadí pro tuto metodu za účelem pracovat, při mapování metadata soubor na disku do paměti voláním [imetadatadispenser::openscope –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) metoda, je nutné zadat `ofReadOnly` příznak a nesmí zadáte `ofWrite` nebo `ofCopyMemory` příznak.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="6ac9c-128">Volba typu souboru mapování pro každý obor je specifická pro danou implementace modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="6ac9c-129">Nejde ji nastavit uživatelem.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-129">It cannot be set by the user.</span></span> <span data-ttu-id="6ac9c-130">Vrátí aktuální implementace modulu CLR vždy `fmFlat` v `pdwMappingType`, ale toto můžete změnit v budoucích verzích modulu CLR nebo v budoucích verzích služby danou verzi.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="6ac9c-131">Vrácená hodnota by měla vždy zkontrolujte v `pdwMappingType`, protože jiné typy bude mít jiné rozložení a odsazení.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="6ac9c-132">Předání hodnotou NULL pro všechny tři parametry není podporována.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="6ac9c-133">Vrátí metoda `E_INVALIDARG`, a jsou vyplněny žádné výstupy.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="6ac9c-134">Mapování typu nebo velikosti oblasti je ignorována, může mít za následek neobvyklé ukončení programu.</span><span class="sxs-lookup"><span data-stu-id="6ac9c-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ac9c-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6ac9c-135">Requirements</span></span>  
 <span data-ttu-id="6ac9c-136">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ac9c-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ac9c-137">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6ac9c-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6ac9c-138">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6ac9c-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6ac9c-139">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ac9c-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ac9c-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ac9c-140">See Also</span></span>  
 [<span data-ttu-id="6ac9c-141">IMetaDataInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ac9c-141">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 [<span data-ttu-id="6ac9c-142">CorFileMapping – výčet</span><span class="sxs-lookup"><span data-stu-id="6ac9c-142">CorFileMapping Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
