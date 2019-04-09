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
ms.openlocfilehash: d9279808e4ad15b693d06ac8a99dd33a609e5a8f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169049"
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="ff716-102">IMetaDataEmit::GetSaveSize – metoda</span><span class="sxs-lookup"><span data-stu-id="ff716-102">IMetaDataEmit::GetSaveSize Method</span></span>
<span data-ttu-id="ff716-103">Získá odhadovaná velikost binárního sestavení a jeho metadata v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="ff716-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff716-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff716-104">Syntax</span></span>  
  
```  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff716-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff716-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="ff716-106">[in] Hodnota [corsavesize –](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) výčet, který určuje, jestli se má získat přesné nebo přibližné velikosti.</span><span class="sxs-lookup"><span data-stu-id="ff716-106">[in] A value of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="ff716-107">Platné jsou jenom tři hodnoty: cssAccurate cssQuick a cssDiscardTransientCAs:</span><span class="sxs-lookup"><span data-stu-id="ff716-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
-   <span data-ttu-id="ff716-108">cssAccurate vrátí přesné uložit velikost ale trvá déle k výpočtu.</span><span class="sxs-lookup"><span data-stu-id="ff716-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
-   <span data-ttu-id="ff716-109">cssQuick vrátí velikost, aby bylo vytvořeno pro zabezpečení, ale trvá méně času k výpočtu.</span><span class="sxs-lookup"><span data-stu-id="ff716-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
-   <span data-ttu-id="ff716-110">říká cssDiscardTransientCAs `GetSaveSize` , že může vyvolat okamžitě discardable vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="ff716-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="ff716-111">[out] Ukazatel na velikost, která je nutná k uložení souboru.</span><span class="sxs-lookup"><span data-stu-id="ff716-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff716-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff716-112">Remarks</span></span>  
 `GetSaveSize` <span data-ttu-id="ff716-113">vypočítá prostor, v bajtech, uložte sestavení a všechny jeho metadata v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="ff716-113">calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="ff716-114">(Volání [imetadataemit::savetostream –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) metody by vygenerovat tento počet bajtů.)</span><span class="sxs-lookup"><span data-stu-id="ff716-114">(A call to the [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="ff716-115">Pokud volající implementuje [imaptoken –](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) rozhraní (prostřednictvím [imetadataemit::sethandler –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) nebo [imetadataemit::merge –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` provede dva průchody přes metadata k optimalizaci a je komprimovat.</span><span class="sxs-lookup"><span data-stu-id="ff716-115">If the caller implements the [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="ff716-116">V opačném případě jsou prováděny žádné optimalizace.</span><span class="sxs-lookup"><span data-stu-id="ff716-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="ff716-117">Pokud se provádí optimalizace, prvním průchodu jednoduše seřadí struktury metadat pro optimalizaci výkonu hledání v době importu.</span><span class="sxs-lookup"><span data-stu-id="ff716-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="ff716-118">Tento krok obvykle vytváří při přesouvání záznamy, s vedlejším účinkem, že nejsou zneplatněny tokeny uchovávají nástrojem pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="ff716-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="ff716-119">Metadata neinformuje volající tyto změny tokenu do po druhé fázi, ale.</span><span class="sxs-lookup"><span data-stu-id="ff716-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="ff716-120">Ve druhé fázi, jsou prováděny různých optimalizací, které slouží ke snížení celkové velikosti metadata, jako je třeba optimalizace tokeny (časná vazba) `mdTypeRef` a `mdMemberRef` tokeny, když je odkaz na typ nebo člen, který je deklarován v aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="ff716-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="ff716-121">V tomto kroku dojde k další várky token mapování.</span><span class="sxs-lookup"><span data-stu-id="ff716-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="ff716-122">Po průchodu, upozorní metadata modulu volající, prostřednictvím svých `IMapToken` rozhraní libovolného změnit hodnoty tokenu.</span><span class="sxs-lookup"><span data-stu-id="ff716-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff716-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff716-123">Requirements</span></span>  
 <span data-ttu-id="ff716-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff716-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff716-125">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ff716-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff716-126">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff716-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="ff716-127">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ff716-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ff716-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff716-128">See also</span></span>

- [<span data-ttu-id="ff716-129">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff716-129">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ff716-130">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff716-130">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
