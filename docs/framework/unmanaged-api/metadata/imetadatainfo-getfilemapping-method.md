---
title: IMetaDataInfo::GetFileMapping – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4c6a9473a698e4635c8b5cc9fb58963334dfd65e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992274"
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="8d582-102">IMetaDataInfo::GetFileMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="8d582-102">IMetaDataInfo::GetFileMapping Method</span></span>
<span data-ttu-id="8d582-103">Získá paměťové oblasti mapovaného souboru a typu mapování.</span><span class="sxs-lookup"><span data-stu-id="8d582-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d582-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d582-104">Syntax</span></span>  
  
```  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d582-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d582-105">Parameters</span></span>  
 `ppvData`  
 <span data-ttu-id="8d582-106">[out] Ukazatel na začátku mapovaného souboru.</span><span class="sxs-lookup"><span data-stu-id="8d582-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="8d582-107">[out] Velikost oblasti pro mapovanou.</span><span class="sxs-lookup"><span data-stu-id="8d582-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="8d582-108">Pokud `pdwMappingType` je `fmFlat`, toto je velikost souboru.</span><span class="sxs-lookup"><span data-stu-id="8d582-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="8d582-109">[out] A [corfilemapping –](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) hodnotu, která určuje typ mapování.</span><span class="sxs-lookup"><span data-stu-id="8d582-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="8d582-110">Aktuální implementace modulu common language runtime (CLR) vždy vrátí `fmFlat`.</span><span class="sxs-lookup"><span data-stu-id="8d582-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="8d582-111">Další hodnoty jsou vyhrazené pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="8d582-111">Other values are reserved for future use.</span></span> <span data-ttu-id="8d582-112">Nicméně vždy byste měli zkontrolovat vrácené hodnoty, protože jiné hodnoty může být povoleno v budoucích verzích nebo vydání služby.</span><span class="sxs-lookup"><span data-stu-id="8d582-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d582-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8d582-113">Return Value</span></span>  
  
|<span data-ttu-id="8d582-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8d582-114">HRESULT</span></span>|<span data-ttu-id="8d582-115">Popis</span><span class="sxs-lookup"><span data-stu-id="8d582-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8d582-116">Všechny výstupy jsou vyplněny.</span><span class="sxs-lookup"><span data-stu-id="8d582-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="8d582-117">NULL byl předán jako hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="8d582-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="8d582-118">Implementace CLR nemůže poskytnout informace o paměťové oblasti.</span><span class="sxs-lookup"><span data-stu-id="8d582-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="8d582-119">Tato situace může nastat z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="8d582-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="8d582-120">-Oboru metadata byla otevřena s `ofWrite` nebo `ofCopyMemory` příznak.</span><span class="sxs-lookup"><span data-stu-id="8d582-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="8d582-121">-Oboru metadat byl otevřen bez `ofReadOnly` příznak.</span><span class="sxs-lookup"><span data-stu-id="8d582-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="8d582-122">– [Imetadatadispenser::openscopeonmemory –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) metoda byla použita k otevření pouze část metadata souboru.</span><span class="sxs-lookup"><span data-stu-id="8d582-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="8d582-123">– Tento soubor není soubor (PE portable executable).</span><span class="sxs-lookup"><span data-stu-id="8d582-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="8d582-124">**Poznámka:**  Tyto podmínky závisí na implementaci modulu CLR a mohou být správné provedení příslušných činností v budoucích verzích CLR.</span><span class="sxs-lookup"><span data-stu-id="8d582-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d582-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d582-125">Remarks</span></span>  
 <span data-ttu-id="8d582-126">Paměť, která `ppvData` odkazuje je platný pouze jako základní obor metadat je otevřený.</span><span class="sxs-lookup"><span data-stu-id="8d582-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="8d582-127">V pořadí pro tuto metodu za účelem práce při mapování metadat souboru na disku do paměti při volání [imetadatadispenser::openscope –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) metoda, je nutné zadat `ofReadOnly` příznak a nesmí určovat `ofWrite` nebo `ofCopyMemory` příznak.</span><span class="sxs-lookup"><span data-stu-id="8d582-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="8d582-128">Volba typu souboru mapování pro každý obor je specifické pro danou implementaci modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="8d582-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="8d582-129">Nejde ji nastavit uživatelem.</span><span class="sxs-lookup"><span data-stu-id="8d582-129">It cannot be set by the user.</span></span> <span data-ttu-id="8d582-130">Vrátí aktuální implementace CLR vždy `fmFlat` v `pdwMappingType`, ale to můžete změnit v budoucích verzí modulu CLR nebo v budoucnu aktualizací service release dané verze.</span><span class="sxs-lookup"><span data-stu-id="8d582-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="8d582-131">Vrácená hodnota by měla vždy zkontrolujte `pdwMappingType`, protože různé typy budou mít různá rozložení a posun.</span><span class="sxs-lookup"><span data-stu-id="8d582-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="8d582-132">Předání hodnoty NULL pro všechny tři parametry není podporován.</span><span class="sxs-lookup"><span data-stu-id="8d582-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="8d582-133">Metoda vrátí `E_INVALIDARG`, a jsou vyplněny žádné výstupy.</span><span class="sxs-lookup"><span data-stu-id="8d582-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="8d582-134">Ignoruje se mapování typu nebo velikosti oblasti může způsobit neobvyklé ukončení programu.</span><span class="sxs-lookup"><span data-stu-id="8d582-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d582-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d582-135">Requirements</span></span>  
 <span data-ttu-id="8d582-136">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d582-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d582-137">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8d582-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8d582-138">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8d582-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8d582-139">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d582-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d582-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d582-140">See also</span></span>

- [<span data-ttu-id="8d582-141">IMetaDataInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d582-141">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [<span data-ttu-id="8d582-142">CorFileMapping – výčet</span><span class="sxs-lookup"><span data-stu-id="8d582-142">CorFileMapping Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
