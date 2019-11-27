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
ms.openlocfilehash: 0cd2071d4410615a08e774ba30e0e8fe8d1fa7c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436171"
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="87af4-102">IMetaDataInfo::GetFileMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="87af4-102">IMetaDataInfo::GetFileMapping Method</span></span>
<span data-ttu-id="87af4-103">Získá oblast paměti mapovaného souboru a typ mapování.</span><span class="sxs-lookup"><span data-stu-id="87af4-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87af4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87af4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87af4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="87af4-105">Parameters</span></span>  
 `ppvData`  
 <span data-ttu-id="87af4-106">mimo Ukazatel na začátek mapovaného souboru.</span><span class="sxs-lookup"><span data-stu-id="87af4-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="87af4-107">mimo Velikost mapované oblasti</span><span class="sxs-lookup"><span data-stu-id="87af4-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="87af4-108">Pokud je `pdwMappingType` `fmFlat`, jedná se o velikost souboru.</span><span class="sxs-lookup"><span data-stu-id="87af4-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="87af4-109">mimo Hodnota [CorFileMapping –](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) , která určuje typ mapování.</span><span class="sxs-lookup"><span data-stu-id="87af4-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="87af4-110">Aktuální implementace modulu CLR (Common Language Runtime) vždy vrací `fmFlat`.</span><span class="sxs-lookup"><span data-stu-id="87af4-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="87af4-111">Jiné hodnoty jsou vyhrazeny pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="87af4-111">Other values are reserved for future use.</span></span> <span data-ttu-id="87af4-112">Měli byste však vždy ověřit vrácenou hodnotu, protože jiné hodnoty mohou být povoleny v budoucích verzích nebo verzích služeb.</span><span class="sxs-lookup"><span data-stu-id="87af4-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87af4-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="87af4-113">Return Value</span></span>  
  
|<span data-ttu-id="87af4-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="87af4-114">HRESULT</span></span>|<span data-ttu-id="87af4-115">Popis</span><span class="sxs-lookup"><span data-stu-id="87af4-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="87af4-116">Všechny výstupy jsou vyplněny.</span><span class="sxs-lookup"><span data-stu-id="87af4-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="87af4-117">Jako hodnota argumentu byla předána hodnota NULL.</span><span class="sxs-lookup"><span data-stu-id="87af4-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="87af4-118">Implementace CLR nemůže poskytovat informace o oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="87af4-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="87af4-119">Tato situace může mít následující důvody:</span><span class="sxs-lookup"><span data-stu-id="87af4-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="87af4-120">– Obor metadat byl otevřen pomocí příznaku `ofWrite` nebo `ofCopyMemory`.</span><span class="sxs-lookup"><span data-stu-id="87af4-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="87af4-121">– Obor metadat byl otevřen bez příznaku `ofReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="87af4-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="87af4-122">– Metoda [IMetaDataDispenser:: OpenScopeOnMemory –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) byla použita k otevření pouze části metadat v souboru.</span><span class="sxs-lookup"><span data-stu-id="87af4-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="87af4-123">– Soubor není soubor přenositelného spustitelného souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="87af4-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="87af4-124">**Poznámka:**  Tyto podmínky závisí na implementaci CLR a jsou pravděpodobně oslabeny v budoucích verzích CLR.</span><span class="sxs-lookup"><span data-stu-id="87af4-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87af4-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87af4-125">Remarks</span></span>  
 <span data-ttu-id="87af4-126">Paměť, na kterou `ppvData` odkazuje, je platná pouze tak dlouho, dokud je otevřený obor metadat.</span><span class="sxs-lookup"><span data-stu-id="87af4-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="87af4-127">Aby tato metoda fungovala, Pokud namapujete metadata souboru na disku do paměti voláním metody [IMetaDataDispenser:: OpenScope –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) , je nutné zadat příznak `ofReadOnly` a není nutné zadat `ofWrite` nebo `ofCopyMemory` příznak.</span><span class="sxs-lookup"><span data-stu-id="87af4-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="87af4-128">Volba typu mapování souborů pro každý obor je specifická pro danou implementaci CLR.</span><span class="sxs-lookup"><span data-stu-id="87af4-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="87af4-129">Tuto hodnotu nemůže nastavit uživatel.</span><span class="sxs-lookup"><span data-stu-id="87af4-129">It cannot be set by the user.</span></span> <span data-ttu-id="87af4-130">Aktuální implementace CLR vždy vrátí `fmFlat` v `pdwMappingType`, ale to se může v budoucích verzích CLR nebo v budoucích vydáních této verze změnit.</span><span class="sxs-lookup"><span data-stu-id="87af4-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="87af4-131">Vždy byste měli kontrolovat vrácenou hodnotu v `pdwMappingType`, protože různé typy budou mít různá rozložení a posuny.</span><span class="sxs-lookup"><span data-stu-id="87af4-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="87af4-132">Předání hodnoty NULL pro některý ze tří parametrů není podporováno.</span><span class="sxs-lookup"><span data-stu-id="87af4-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="87af4-133">Metoda vrátí `E_INVALIDARG`a žádný z výstupů není vyplněn.</span><span class="sxs-lookup"><span data-stu-id="87af4-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="87af4-134">Ignorování typu mapování nebo velikost oblasti může způsobit neobvyklé ukončení programu.</span><span class="sxs-lookup"><span data-stu-id="87af4-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87af4-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="87af4-135">Requirements</span></span>  
 <span data-ttu-id="87af4-136">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87af4-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87af4-137">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="87af4-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="87af4-138">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="87af4-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="87af4-139">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87af4-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87af4-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87af4-140">See also</span></span>

- [<span data-ttu-id="87af4-141">IMetaDataInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87af4-141">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [<span data-ttu-id="87af4-142">CorFileMapping – výčet</span><span class="sxs-lookup"><span data-stu-id="87af4-142">CorFileMapping Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
