---
title: Init – metoda
ms.date: 03/30/2017
api_name:
- IALink.Init
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- Init
helpviewer_keywords:
- Init method
ms.assetid: e48b5c64-049f-4f93-ad87-d07ae9cd5845
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf96770dd58c9b84596c082a615f626ec723cc6c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787245"
---
# <a name="init-method"></a><span data-ttu-id="ad43b-102">Init – metoda</span><span class="sxs-lookup"><span data-stu-id="ad43b-102">Init Method</span></span>
<span data-ttu-id="ad43b-103">Připraví objekty implementující [rozhraní IALink –](ialink-interface.md) pro použití.</span><span class="sxs-lookup"><span data-stu-id="ad43b-103">Prepares objects implementing the [IALink Interface](ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad43b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad43b-104">Syntax</span></span>  
  
```cpp  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad43b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad43b-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="ad43b-106">Ukazatel [rozhraní IMetaDataDispenserEx](../metadata/imetadatadispenserex-interface.md) na zásobník metadat.</span><span class="sxs-lookup"><span data-stu-id="ad43b-106">[IMetaDataDispenserEx Interface](../metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="ad43b-107">Ukazatel [rozhraní IMetaDataError –](../metadata/imetadataerror-interface.md) na volitelné rozhraní pro zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="ad43b-107">[IMetaDataError Interface](../metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad43b-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ad43b-108">Return Value</span></span>  
 <span data-ttu-id="ad43b-109">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="ad43b-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad43b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad43b-110">Requirements</span></span>  
 <span data-ttu-id="ad43b-111">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="ad43b-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad43b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad43b-112">See also</span></span>

- [<span data-ttu-id="ad43b-113">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad43b-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="ad43b-114">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad43b-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="ad43b-115">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="ad43b-115">ALink API</span></span>](index.md)
