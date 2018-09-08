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
ms.openlocfilehash: faa9bc412e67e0e49ee969bd8b246a424fe628a0
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44193273"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="8ef18-102">IMetaDataEmit::ApplyEditAndContinue – metoda</span><span class="sxs-lookup"><span data-stu-id="8ef18-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="8ef18-103">Aktualizuje aktuální obor sestavení změny provedené v Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="8ef18-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ef18-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ef18-104">Syntax</span></span>  
  
```  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ef18-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ef18-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="8ef18-106">\[v\] ukazatel [IUnknown](/cpp/atl/iunknown) objekt, který reprezentuje delta metadat ze souboru (PE portable executable).</span><span class="sxs-lookup"><span data-stu-id="8ef18-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="8ef18-107">Metadata rozdílů je blok metadata, která obsahuje změny, které byly provedeny na kopii skutečného metadata modulu.</span><span class="sxs-lookup"><span data-stu-id="8ef18-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ef18-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ef18-108">Requirements</span></span>  
 <span data-ttu-id="8ef18-109">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ef18-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ef18-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8ef18-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8ef18-111">**Knihovna:** použit jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8ef18-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ef18-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ef18-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef18-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ef18-113">See Also</span></span>  
 [<span data-ttu-id="8ef18-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ef18-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="8ef18-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ef18-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
