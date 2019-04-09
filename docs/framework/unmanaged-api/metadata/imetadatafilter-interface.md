---
title: IMetaDataFilter – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataFilter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter
helpviewer_keywords:
- IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4196ff2cb2d4ebc401076f603a8a7fdc9b9c76ea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143790"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="3ea35-102">IMetaDataFilter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3ea35-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="3ea35-103">Poskytuje metody pro označení a filtrování tokeny metadat předcházet opakování akce, které již byly provedeny.</span><span class="sxs-lookup"><span data-stu-id="3ea35-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3ea35-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3ea35-104">Methods</span></span>  
  
|<span data-ttu-id="3ea35-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3ea35-105">Method</span></span>|<span data-ttu-id="3ea35-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3ea35-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3ea35-107">IsTokenMarked – metoda</span><span class="sxs-lookup"><span data-stu-id="3ea35-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="3ea35-108">Získá hodnotu označující, zda token Zadaná metadata byla zpracována.</span><span class="sxs-lookup"><span data-stu-id="3ea35-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="3ea35-109">MarkToken – metoda</span><span class="sxs-lookup"><span data-stu-id="3ea35-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="3ea35-110">Nastaví hodnotu označující, že token Zadaná metadata byla zpracována.</span><span class="sxs-lookup"><span data-stu-id="3ea35-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="3ea35-111">UnmarkAll – metoda</span><span class="sxs-lookup"><span data-stu-id="3ea35-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="3ea35-112">Odstraní značky zpracování ze všech tokenů v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="3ea35-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3ea35-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3ea35-113">Requirements</span></span>  
 <span data-ttu-id="3ea35-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ea35-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ea35-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3ea35-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3ea35-116">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3ea35-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="3ea35-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="3ea35-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3ea35-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ea35-118">See also</span></span>

- [<span data-ttu-id="3ea35-119">Rozhraní metadat</span><span class="sxs-lookup"><span data-stu-id="3ea35-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
