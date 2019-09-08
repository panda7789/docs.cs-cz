---
title: IInstallReferenceEnum – rozhraní
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum
helpviewer_keywords:
- IInstallReferenceEnum interface [.NET Framework fusion]
ms.assetid: 2863b33b-a541-462c-bbe8-702a2832898e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d29b9e2a9b9022f682065816a62734d6c5b2d62
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796406"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="1197e-102">IInstallReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1197e-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="1197e-103">Představuje enumerátor pro odkazovaná sestavení nainstalovaná v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="1197e-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1197e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1197e-104">Syntax</span></span>  
  
```cpp  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1197e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1197e-105">Methods</span></span>  
  
|<span data-ttu-id="1197e-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="1197e-106">Method</span></span>|<span data-ttu-id="1197e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1197e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1197e-108">GetNextInstallReferenceItem – metoda</span><span class="sxs-lookup"><span data-stu-id="1197e-108">GetNextInstallReferenceItem Method</span></span>](iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="1197e-109">Získá ukazatel na další `IInstallReferenceItem` obsaženou v tomto. `IInstallReferenceEnum`</span><span class="sxs-lookup"><span data-stu-id="1197e-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1197e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1197e-110">Requirements</span></span>  
 <span data-ttu-id="1197e-111">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1197e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1197e-112">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="1197e-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1197e-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1197e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1197e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1197e-114">See also</span></span>

- [<span data-ttu-id="1197e-115">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="1197e-115">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="1197e-116">IInstallReferenceItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1197e-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
