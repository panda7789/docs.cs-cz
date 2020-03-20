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
ms.openlocfilehash: 0f5bdf97132c05e765cd6fa423a19bb996105d28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175262"
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="a9540-102">IMetaDataInfo::GetFileMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="a9540-102">IMetaDataInfo::GetFileMapping Method</span></span>
<span data-ttu-id="a9540-103">Získá oblast paměti mapovaného souboru a typ mapování.</span><span class="sxs-lookup"><span data-stu-id="a9540-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9540-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9540-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,
    [out] ULONGLONG            *pcbData,
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9540-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9540-105">Parameters</span></span>  
 `ppvData`  
 <span data-ttu-id="a9540-106">[out] Ukazatel na začátek mapovaného souboru.</span><span class="sxs-lookup"><span data-stu-id="a9540-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="a9540-107">[out] Velikost mapované oblasti.</span><span class="sxs-lookup"><span data-stu-id="a9540-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="a9540-108">Pokud `pdwMappingType` `fmFlat`je , jedná se o velikost souboru.</span><span class="sxs-lookup"><span data-stu-id="a9540-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="a9540-109">[out] Hodnota [CorFileMapping,](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) která označuje typ mapování.</span><span class="sxs-lookup"><span data-stu-id="a9540-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="a9540-110">Aktuální implementace cltime společného jazyka (CLR) vždy vrátí `fmFlat`.</span><span class="sxs-lookup"><span data-stu-id="a9540-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="a9540-111">Ostatní hodnoty jsou vyhrazeny pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="a9540-111">Other values are reserved for future use.</span></span> <span data-ttu-id="a9540-112">Však měli byste vždy ověřit vrácenou hodnotu, protože jiné hodnoty mohou být povoleny v budoucích verzích nebo vydání služby.</span><span class="sxs-lookup"><span data-stu-id="a9540-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9540-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a9540-113">Return Value</span></span>  
  
|<span data-ttu-id="a9540-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a9540-114">HRESULT</span></span>|<span data-ttu-id="a9540-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a9540-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a9540-116">Všechny výstupy jsou vyplněny.</span><span class="sxs-lookup"><span data-stu-id="a9540-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="a9540-117">Hodnota NULL byla předána jako hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="a9540-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="a9540-118">Implementace CLR nemůže poskytnout informace o oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="a9540-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="a9540-119">K tomu může dojít z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="a9540-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="a9540-120">- Obor metadat byl otevřen `ofWrite` `ofCopyMemory` s příznakem nebo.</span><span class="sxs-lookup"><span data-stu-id="a9540-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="a9540-121">- Obor metadat byl otevřen `ofReadOnly` bez vlajky.</span><span class="sxs-lookup"><span data-stu-id="a9540-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="a9540-122">- Metoda [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) byla použita k otevření pouze části souboru metadat.</span><span class="sxs-lookup"><span data-stu-id="a9540-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="a9540-123">- Soubor není přenosný spustitelný soubor (PE).</span><span class="sxs-lookup"><span data-stu-id="a9540-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="a9540-124">**Poznámka:**  Tyto podmínky závisí na implementaci CLR a pravděpodobně budou oslabeny v budoucích verzích CLR.</span><span class="sxs-lookup"><span data-stu-id="a9540-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9540-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a9540-125">Remarks</span></span>  
 <span data-ttu-id="a9540-126">Paměť, `ppvData` která odkazuje na je platný pouze tak dlouho, dokud je otevřen základní obor metadat.</span><span class="sxs-lookup"><span data-stu-id="a9540-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="a9540-127">Aby tato metoda fungovala, při mapování metadat souboru na disku do paměti voláním [metody IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) je nutné zadat `ofReadOnly` příznak a nesmíte zadat `ofWrite` příznak nebo. `ofCopyMemory`</span><span class="sxs-lookup"><span data-stu-id="a9540-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="a9540-128">Volba typu mapování souborů pro každý obor je specifická pro danou implementaci CLR.</span><span class="sxs-lookup"><span data-stu-id="a9540-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="a9540-129">Nemůže být nastavena uživatelem.</span><span class="sxs-lookup"><span data-stu-id="a9540-129">It cannot be set by the user.</span></span> <span data-ttu-id="a9540-130">Aktuální implementace CLR vždy `fmFlat` vrátí `pdwMappingType`v , ale to může změnit v budoucích verzích CLR nebo v budoucích verzích služby dané verze.</span><span class="sxs-lookup"><span data-stu-id="a9540-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="a9540-131">Vrácenou hodnotu byste `pdwMappingType`měli vždy zkontrolovat v souboru , protože různé typy budou mít různá rozložení a posuny.</span><span class="sxs-lookup"><span data-stu-id="a9540-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="a9540-132">Předávání hodnoty NULL pro některý ze tří parametrů není podporováno.</span><span class="sxs-lookup"><span data-stu-id="a9540-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="a9540-133">Metoda vrátí `E_INVALIDARG`a žádný z výstupů jsou vyplněny.</span><span class="sxs-lookup"><span data-stu-id="a9540-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="a9540-134">Ignorování typu mapování nebo velikosti oblasti může mít za následek abnormální ukončení programu.</span><span class="sxs-lookup"><span data-stu-id="a9540-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9540-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a9540-135">Requirements</span></span>  
 <span data-ttu-id="a9540-136">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9540-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9540-137">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="a9540-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a9540-138">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9540-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a9540-139">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9540-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9540-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9540-140">See also</span></span>

- [<span data-ttu-id="a9540-141">IMetaDataInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9540-141">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [<span data-ttu-id="a9540-142">CorFileMapping – výčet</span><span class="sxs-lookup"><span data-stu-id="a9540-142">CorFileMapping Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
