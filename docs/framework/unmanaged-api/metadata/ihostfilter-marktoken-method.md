---
title: IHostFilter::MarkToken – metoda
ms.date: 03/30/2017
api_name:
- IHostFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostFilter::MarkToken
helpviewer_keywords:
- MarkToken method, IHostFilter interface [.NET Framework metadata]
- IHostFilter::MarkToken method [.NET Framework metadata]
ms.assetid: d7061343-d0a3-4fd5-b312-61974f98bd62
topic_type:
- apiref
ms.openlocfilehash: 11529ce896f265f2b200fa6e511d4b913e9147c8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008219"
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="6459f-102">IHostFilter::MarkToken – metoda</span><span class="sxs-lookup"><span data-stu-id="6459f-102">IHostFilter::MarkToken Method</span></span>
<span data-ttu-id="6459f-103">Indikuje, že se zpracuje zadaný token metadat.</span><span class="sxs-lookup"><span data-stu-id="6459f-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6459f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6459f-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6459f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6459f-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="6459f-106">pro Token metadat, který má být zpracován.</span><span class="sxs-lookup"><span data-stu-id="6459f-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6459f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6459f-107">Remarks</span></span>  
 <span data-ttu-id="6459f-108">Obvykle chcete zpracovat token, pokud je v oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="6459f-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="6459f-109">`MarkToken`Metoda je předána modulu metadat pomocí metody [IMetaDataEmit:: SetHandler –](imetadataemit-sethandler-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6459f-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6459f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6459f-110">Requirements</span></span>  
 <span data-ttu-id="6459f-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6459f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6459f-112">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6459f-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6459f-113">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="6459f-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6459f-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6459f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6459f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="6459f-115">See also</span></span>

- [<span data-ttu-id="6459f-116">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="6459f-116">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="6459f-117">IHostFilter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6459f-117">IHostFilter Interface</span></span>](ihostfilter-interface.md)
