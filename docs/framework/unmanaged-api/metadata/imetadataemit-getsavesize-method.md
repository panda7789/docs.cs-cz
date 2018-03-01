---
title: "IMetaDataEmit::GetSaveSize – metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7585f6adbca97b252fdad90276b0cd422d32c04a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="66812-102">IMetaDataEmit::GetSaveSize – metoda</span><span class="sxs-lookup"><span data-stu-id="66812-102">IMetaDataEmit::GetSaveSize Method</span></span>
<span data-ttu-id="66812-103">Získá binární odhadovanou velikost sestavení a jeho metadata v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="66812-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66812-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66812-104">Syntax</span></span>  
  
```  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66812-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66812-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="66812-106">[v] Hodnota [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) výčtu, která určuje, zda chcete-li získat přesné nebo přibližnou velikost.</span><span class="sxs-lookup"><span data-stu-id="66812-106">[in] A value of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="66812-107">Jsou platné pouze tří hodnot: cssAccurate, cssQuick a cssDiscardTransientCAs:</span><span class="sxs-lookup"><span data-stu-id="66812-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
-   <span data-ttu-id="66812-108">cssAccurate vrací přesnou uložit velikost, ale trvá déle k výpočtu.</span><span class="sxs-lookup"><span data-stu-id="66812-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
-   <span data-ttu-id="66812-109">cssQuick vrátí velikost, vyplní pro zabezpečení, ale zabere to méně času k výpočtu.</span><span class="sxs-lookup"><span data-stu-id="66812-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
-   <span data-ttu-id="66812-110">informuje cssDiscardTransientCAs `GetSaveSize` , můžete vyvolat rychle discardable vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="66812-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="66812-111">[out] Ukazatel na velikost, který je potřeba soubor uložte.</span><span class="sxs-lookup"><span data-stu-id="66812-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66812-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66812-112">Remarks</span></span>  
 <span data-ttu-id="66812-113">`GetSaveSize`vypočítá na místo, v bajtech pro uložení sestavení a všechny jeho metadata v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="66812-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="66812-114">(Volání [imetadataemit::savetostream –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) metoda by emitování tento počet bajtů.)</span><span class="sxs-lookup"><span data-stu-id="66812-114">(A call to the [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="66812-115">Pokud má volající implementuje [imaptoken –](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) rozhraní (prostřednictvím [imetadataemit::sethandler –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) nebo [imetadataemit::merge –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` provede dvou průchodů přes metadata optimalizace a je komprimovat.</span><span class="sxs-lookup"><span data-stu-id="66812-115">If the caller implements the [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="66812-116">Jinak jsou prováděny žádné optimalizace.</span><span class="sxs-lookup"><span data-stu-id="66812-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="66812-117">Pokud se provádí optimalizace, první fáze jednoduše seřadí struktury metadat pro optimalizaci výkonu vyhledání v době importu.</span><span class="sxs-lookup"><span data-stu-id="66812-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="66812-118">Tento krok se obvykle výsledkem přesunutí záznamy problému s vedlejším účinkem, že jsou zneplatněny tokeny uchovávají nástrojem pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="66812-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="66812-119">Metadata neinformuje volající tyto změny tokenu až po druhé fázi, ale.</span><span class="sxs-lookup"><span data-stu-id="66812-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="66812-120">V druhé fázi se provádí různé optimalizace, které slouží ke snížení celkové velikosti metadata, například pro optimalizaci tokeny (časná vazba) `mdTypeRef` a `mdMemberRef` tokeny, když je odkaz na typ nebo člen, který je v deklarována aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="66812-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="66812-121">V tomto průchodu dojde k jiné zaokrouhlit tokenu mapování.</span><span class="sxs-lookup"><span data-stu-id="66812-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="66812-122">Po tomto průchodu modul metadata upozorní volající, prostřednictvím jeho `IMapToken` rozhraní všech změnit hodnoty tokenu.</span><span class="sxs-lookup"><span data-stu-id="66812-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66812-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66812-123">Requirements</span></span>  
 <span data-ttu-id="66812-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66812-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66812-125">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="66812-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="66812-126">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="66812-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66812-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66812-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66812-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="66812-128">See Also</span></span>  
 [<span data-ttu-id="66812-129">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66812-129">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="66812-130">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66812-130">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
