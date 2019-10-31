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
ms.openlocfilehash: d3f7c24b4bd373924c44dbc0490c890e7f1322bd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131736"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="80bf0-102">IInstallReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="80bf0-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="80bf0-103">Představuje enumerátor pro odkazovaná sestavení nainstalovaná v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="80bf0-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80bf0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80bf0-104">Syntax</span></span>  
  
```cpp  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="80bf0-105">Metody</span><span class="sxs-lookup"><span data-stu-id="80bf0-105">Methods</span></span>  
  
|<span data-ttu-id="80bf0-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="80bf0-106">Method</span></span>|<span data-ttu-id="80bf0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="80bf0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="80bf0-108">GetNextInstallReferenceItem – metoda</span><span class="sxs-lookup"><span data-stu-id="80bf0-108">GetNextInstallReferenceItem Method</span></span>](iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="80bf0-109">Získá ukazatel na další `IInstallReferenceItem` obsažený v tomto `IInstallReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="80bf0-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="80bf0-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="80bf0-110">Requirements</span></span>  
 <span data-ttu-id="80bf0-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80bf0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80bf0-112">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="80bf0-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="80bf0-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80bf0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80bf0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="80bf0-114">See also</span></span>

- [<span data-ttu-id="80bf0-115">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="80bf0-115">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="80bf0-116">IInstallReferenceItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="80bf0-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
