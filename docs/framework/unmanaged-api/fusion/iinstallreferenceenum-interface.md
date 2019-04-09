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
ms.openlocfilehash: 35faeb69e864a428dc40394ad89a7d50b95bbcab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103321"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="b38c5-102">IInstallReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b38c5-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="b38c5-103">Představuje enumerátor pro odkazovaná sestavení nainstalována v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="b38c5-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b38c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b38c5-104">Syntax</span></span>  
  
```  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b38c5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b38c5-105">Methods</span></span>  
  
|<span data-ttu-id="b38c5-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b38c5-106">Method</span></span>|<span data-ttu-id="b38c5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b38c5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b38c5-108">GetNextInstallReferenceItem – metoda</span><span class="sxs-lookup"><span data-stu-id="b38c5-108">GetNextInstallReferenceItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="b38c5-109">Získá ukazatel na další `IInstallReferenceItem` obsažené v tomto `IInstallReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="b38c5-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b38c5-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b38c5-110">Requirements</span></span>  
 <span data-ttu-id="b38c5-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b38c5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b38c5-112">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b38c5-112">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="b38c5-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b38c5-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b38c5-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b38c5-114">See also</span></span>

- [<span data-ttu-id="b38c5-115">Rozhraní fúze</span><span class="sxs-lookup"><span data-stu-id="b38c5-115">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="b38c5-116">IInstallReferenceItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b38c5-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
