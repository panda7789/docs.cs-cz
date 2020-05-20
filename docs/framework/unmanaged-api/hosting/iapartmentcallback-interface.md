---
title: IApartmentCallback – rozhraní
ms.date: 03/30/2017
api_name:
- IApartmentCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IApartmentCallback
helpviewer_keywords:
- IApartmentCallback interface [.NET Framework hosting]
ms.assetid: 57c33c58-bf0b-4533-b569-e6a682d02cba
topic_type:
- apiref
ms.openlocfilehash: fbf501d906ecc0bf55719fa33d1af2d4db1cc2ef
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617086"
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="adb8e-102">IApartmentCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="adb8e-102">IApartmentCallback Interface</span></span>
<span data-ttu-id="adb8e-103">Poskytuje metody pro provádění zpětných volání v rámci objektu apartment.</span><span class="sxs-lookup"><span data-stu-id="adb8e-103">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="adb8e-104">*Apartment* je logický kontejner v rámci procesu pro objekty, které sdílejí stejné požadavky na přístup k vláknům.</span><span class="sxs-lookup"><span data-stu-id="adb8e-104">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="adb8e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="adb8e-105">Methods</span></span>  
  
|<span data-ttu-id="adb8e-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="adb8e-106">Method</span></span>|<span data-ttu-id="adb8e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="adb8e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="adb8e-108">DoCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="adb8e-108">DoCallback Method</span></span>](iapartmentcallback-docallback-method.md)|<span data-ttu-id="adb8e-109">Spustí zadanou funkci v rámci objektu apartment.</span><span class="sxs-lookup"><span data-stu-id="adb8e-109">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="adb8e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="adb8e-110">Requirements</span></span>  
 <span data-ttu-id="adb8e-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adb8e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adb8e-112">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="adb8e-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="adb8e-113">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="adb8e-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="adb8e-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adb8e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adb8e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="adb8e-115">See also</span></span>

- [<span data-ttu-id="adb8e-116">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="adb8e-116">Hosting Interfaces</span></span>](hosting-interfaces.md)
