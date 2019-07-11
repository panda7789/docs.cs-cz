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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7337222f7f419c68ae21d604d1673158acca85ba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777388"
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="e742e-102">IMetaDataEmit::GetSaveSize – metoda</span><span class="sxs-lookup"><span data-stu-id="e742e-102">IMetaDataEmit::GetSaveSize Method</span></span>
<span data-ttu-id="e742e-103">Získá odhadovaná velikost binárního sestavení a jeho metadata v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="e742e-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e742e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e742e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e742e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e742e-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="e742e-106">[in] Hodnota [corsavesize –](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) výčet, který určuje, jestli se má získat přesné nebo přibližné velikosti.</span><span class="sxs-lookup"><span data-stu-id="e742e-106">[in] A value of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="e742e-107">Platné jsou jenom tři hodnoty: cssAccurate cssQuick a cssDiscardTransientCAs:</span><span class="sxs-lookup"><span data-stu-id="e742e-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
- <span data-ttu-id="e742e-108">cssAccurate vrátí přesné uložit velikost ale trvá déle k výpočtu.</span><span class="sxs-lookup"><span data-stu-id="e742e-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
- <span data-ttu-id="e742e-109">cssQuick vrátí velikost, aby bylo vytvořeno pro zabezpečení, ale trvá méně času k výpočtu.</span><span class="sxs-lookup"><span data-stu-id="e742e-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
- <span data-ttu-id="e742e-110">říká cssDiscardTransientCAs `GetSaveSize` , že může vyvolat okamžitě discardable vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="e742e-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="e742e-111">[out] Ukazatel na velikost, která je nutná k uložení souboru.</span><span class="sxs-lookup"><span data-stu-id="e742e-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e742e-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e742e-112">Remarks</span></span>  
 <span data-ttu-id="e742e-113">`GetSaveSize` vypočítá prostor, v bajtech, uložte sestavení a všechny jeho metadata v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="e742e-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="e742e-114">(Volání [imetadataemit::savetostream –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) metody by vygenerovat tento počet bajtů.)</span><span class="sxs-lookup"><span data-stu-id="e742e-114">(A call to the [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="e742e-115">Pokud volající implementuje [imaptoken –](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) rozhraní (prostřednictvím [imetadataemit::sethandler –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) nebo [imetadataemit::merge –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` provede dva průchody přes metadata k optimalizaci a je komprimovat.</span><span class="sxs-lookup"><span data-stu-id="e742e-115">If the caller implements the [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="e742e-116">V opačném případě jsou prováděny žádné optimalizace.</span><span class="sxs-lookup"><span data-stu-id="e742e-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="e742e-117">Pokud se provádí optimalizace, prvním průchodu jednoduše seřadí struktury metadat pro optimalizaci výkonu hledání v době importu.</span><span class="sxs-lookup"><span data-stu-id="e742e-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="e742e-118">Tento krok obvykle vytváří při přesouvání záznamy, s vedlejším účinkem, že nejsou zneplatněny tokeny uchovávají nástrojem pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="e742e-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="e742e-119">Metadata neinformuje volající tyto změny tokenu do po druhé fázi, ale.</span><span class="sxs-lookup"><span data-stu-id="e742e-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="e742e-120">Ve druhé fázi, jsou prováděny různých optimalizací, které slouží ke snížení celkové velikosti metadata, jako je třeba optimalizace tokeny (časná vazba) `mdTypeRef` a `mdMemberRef` tokeny, když je odkaz na typ nebo člen, který je deklarován v aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="e742e-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="e742e-121">V tomto kroku dojde k další várky token mapování.</span><span class="sxs-lookup"><span data-stu-id="e742e-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="e742e-122">Po průchodu, upozorní metadata modulu volající, prostřednictvím svých `IMapToken` rozhraní libovolného změnit hodnoty tokenu.</span><span class="sxs-lookup"><span data-stu-id="e742e-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e742e-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e742e-123">Requirements</span></span>  
 <span data-ttu-id="e742e-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e742e-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e742e-125">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e742e-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e742e-126">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e742e-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e742e-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e742e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e742e-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e742e-128">See also</span></span>

- [<span data-ttu-id="e742e-129">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e742e-129">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e742e-130">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e742e-130">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
