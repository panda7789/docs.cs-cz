---
title: IMetaDataEmit::GetSaveSize – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type:
- apiref
ms.openlocfilehash: 22c0a317777a12294ba7a90f7af1ceeca3ad0a47
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009259"
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="5d91e-102">IMetaDataEmit::GetSaveSize – metoda</span><span class="sxs-lookup"><span data-stu-id="5d91e-102">IMetaDataEmit::GetSaveSize Method</span></span>
<span data-ttu-id="5d91e-103">Získá odhadovanou binární velikost sestavení a jeho metadat v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="5d91e-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d91e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d91e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d91e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d91e-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="5d91e-106">pro Hodnota výčtu [CorSaveSize –](corsavesize-enumeration.md) , která určuje, zda má být získána přesná nebo Přibližná velikost.</span><span class="sxs-lookup"><span data-stu-id="5d91e-106">[in] A value of the [CorSaveSize](corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="5d91e-107">Platné jsou jenom tři hodnoty: cssAccurate, cssQuick a cssDiscardTransientCAs:</span><span class="sxs-lookup"><span data-stu-id="5d91e-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
- <span data-ttu-id="5d91e-108">cssAccurate vrací přesný formát pro uložení, ale trvá déle, než se vypočítá.</span><span class="sxs-lookup"><span data-stu-id="5d91e-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
- <span data-ttu-id="5d91e-109">cssQuick vrací velikost, doplněnou z důvodu bezpečnosti, ale pro výpočet trvá méně času.</span><span class="sxs-lookup"><span data-stu-id="5d91e-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
- <span data-ttu-id="5d91e-110">cssDiscardTransientCAs informuje o `GetSaveSize` tom, že může vyvolávat nehodíelné vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="5d91e-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="5d91e-111">mimo Ukazatel na velikost, která je nutná k uložení souboru.</span><span class="sxs-lookup"><span data-stu-id="5d91e-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d91e-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5d91e-112">Remarks</span></span>  
 <span data-ttu-id="5d91e-113">`GetSaveSize`vypočítá požadované místo v bajtech pro uložení sestavení a všech jeho metadat v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="5d91e-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="5d91e-114">(Volání metody [IMetaDataEmit:: SaveToStream –](imetadataemit-savetostream-method.md) vygenerovalo tento počet bajtů.)</span><span class="sxs-lookup"><span data-stu-id="5d91e-114">(A call to the [IMetaDataEmit::SaveToStream](imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="5d91e-115">Pokud volající implementuje rozhraní [IMapToken –](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) (prostřednictvím [IMetaDataEmit:: SetHandler –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) nebo [IMetaDataEmit:: Merge](imetadataemit-merge-method.md)), provede `GetSaveSize` dva průchody metadaty za účelem optimalizace a komprimace.</span><span class="sxs-lookup"><span data-stu-id="5d91e-115">If the caller implements the [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="5d91e-116">V opačném případě se neprovede žádné optimalizace.</span><span class="sxs-lookup"><span data-stu-id="5d91e-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="5d91e-117">Pokud je provedena optimalizace, první průchod jednoduše seřadí struktury metadat a optimalizuje výkon při importu.</span><span class="sxs-lookup"><span data-stu-id="5d91e-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="5d91e-118">Tento krok obvykle má za následek přesun záznamů s vedlejším účinkem, kdy jsou tokeny uchovávané nástrojem pro budoucí odkazy neověřené.</span><span class="sxs-lookup"><span data-stu-id="5d91e-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="5d91e-119">Metadata neoznamují volajícím těchto změn tokenů do té doby, než je však druhý úspěch.</span><span class="sxs-lookup"><span data-stu-id="5d91e-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="5d91e-120">Ve druhém průchodu jsou provedeny různé optimalizace, které mají omezit celkovou velikost metadat, jako je například optimalizace nepřítomnosti (předčasné vázání) `mdTypeRef` a `mdMemberRef` tokeny, pokud je odkaz na typ nebo člen deklarovaný v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="5d91e-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="5d91e-121">V tomto průchodu dojde k dalšímu zaokrouhlení mapování tokenů.</span><span class="sxs-lookup"><span data-stu-id="5d91e-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="5d91e-122">Po tomto průchodu modul metadata Engine upozorní volajícího prostřednictvím jeho `IMapToken` rozhraní o jakékoli změněné hodnoty tokenu.</span><span class="sxs-lookup"><span data-stu-id="5d91e-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d91e-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d91e-123">Requirements</span></span>  
 <span data-ttu-id="5d91e-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d91e-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d91e-125">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5d91e-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5d91e-126">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="5d91e-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d91e-127">**Verze .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d91e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d91e-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d91e-128">See also</span></span>

- [<span data-ttu-id="5d91e-129">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d91e-129">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="5d91e-130">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d91e-130">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
