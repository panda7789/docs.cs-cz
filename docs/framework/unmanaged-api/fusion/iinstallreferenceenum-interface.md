---
title: "IInstallReferenceEnum – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IInstallReferenceEnum
api_location: fusion.dll
api_type: COM
f1_keywords: IInstallReferenceEnum
helpviewer_keywords: IInstallReferenceEnum interface [.NET Framework fusion]
ms.assetid: 2863b33b-a541-462c-bbe8-702a2832898e
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d3847d06c77a92eb6e63542f03405ca0cb9c9560
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="62d45-102">IInstallReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62d45-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="62d45-103">Představuje enumerátor pro odkazované sestavení nainstalované v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="62d45-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62d45-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62d45-104">Syntax</span></span>  
  
```  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="62d45-105">Metody</span><span class="sxs-lookup"><span data-stu-id="62d45-105">Methods</span></span>  
  
|<span data-ttu-id="62d45-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="62d45-106">Method</span></span>|<span data-ttu-id="62d45-107">Popis</span><span class="sxs-lookup"><span data-stu-id="62d45-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="62d45-108">Getnextinstallreferenceitem – metoda</span><span class="sxs-lookup"><span data-stu-id="62d45-108">GetNextInstallReferenceItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="62d45-109">Získá ukazatel na další `IInstallReferenceItem` obsažené v tomto `IInstallReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="62d45-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="62d45-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62d45-110">Requirements</span></span>  
 <span data-ttu-id="62d45-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62d45-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62d45-112">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="62d45-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="62d45-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62d45-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62d45-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="62d45-114">See Also</span></span>  
 [<span data-ttu-id="62d45-115">Rozhraní fúze</span><span class="sxs-lookup"><span data-stu-id="62d45-115">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="62d45-116">Iinstallreferenceitem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62d45-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
