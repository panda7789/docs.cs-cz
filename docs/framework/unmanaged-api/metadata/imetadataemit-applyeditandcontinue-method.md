---
title: IMetaDataEmit::ApplyEditAndContinue – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.ApplyEditAndContinue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::ApplyEditAndContinue
helpviewer_keywords:
- ApplyEditAndContinue method [.NET Framework metadata]
- IMetaDataEmit::ApplyEditAndContinue method [.NET Framework metadata]
ms.assetid: 35991289-f389-495d-8caa-a6384fb1d557
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c15c554e0ec135b33d671a83b5e27d0a2a89b731
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444253"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="a343b-102">IMetaDataEmit::ApplyEditAndContinue – metoda</span><span class="sxs-lookup"><span data-stu-id="a343b-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="a343b-103">Aktualizuje aktuální obor sestavení změny provedené v Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="a343b-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a343b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a343b-104">Syntax</span></span>  
  
```  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a343b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a343b-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="a343b-106">[v] Ukazatel na <<!--zzxref:IUnknown --> `IUnknown`> objekt, který reprezentuje rozdílů metadat ze souboru přenosné spustitelný soubor (PE).</span><span class="sxs-lookup"><span data-stu-id="a343b-106">[in] Pointer to an <<!--zzxref:IUnknown --> `IUnknown`> object that represents the delta metadata from the portable executable (PE) file.</span></span>  
  
 <span data-ttu-id="a343b-107">Metadata rozdílů je blok metadata, která obsahuje změny, které byly provedeny kopii skutečného metadat modulu.</span><span class="sxs-lookup"><span data-stu-id="a343b-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a343b-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a343b-108">Requirements</span></span>  
 <span data-ttu-id="a343b-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a343b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a343b-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a343b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a343b-111">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a343b-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a343b-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a343b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a343b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a343b-113">See Also</span></span>  
 [<span data-ttu-id="a343b-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a343b-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a343b-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a343b-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
