---
title: IMetaDataFilter::MarkToken – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::MarkToken
helpviewer_keywords:
- IMetaDataFilter::MarkToken method [.NET Framework metadata]
- MarkToken method, IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: bd492834-6529-4d39-b93d-f8cdbd3e297f
topic_type:
- apiref
ms.openlocfilehash: 28a5f79f6fa8d25fd254c4093b0f76e0308edbad
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492522"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="7961d-102">IMetaDataFilter::MarkToken – metoda</span><span class="sxs-lookup"><span data-stu-id="7961d-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="7961d-103">Nastaví hodnotu označující, že zadaný token metadat byl zpracován.</span><span class="sxs-lookup"><span data-stu-id="7961d-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7961d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7961d-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7961d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7961d-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="7961d-106">pro Token, který má být označen jako zpracovaný.</span><span class="sxs-lookup"><span data-stu-id="7961d-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7961d-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7961d-107">Requirements</span></span>  
 <span data-ttu-id="7961d-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7961d-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7961d-109">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7961d-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7961d-110">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="7961d-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7961d-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7961d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7961d-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7961d-112">See also</span></span>

- [<span data-ttu-id="7961d-113">IMetaDataFilter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7961d-113">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
