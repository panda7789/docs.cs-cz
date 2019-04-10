---
title: Funkce CreateIDispatchSTAForwarder (WPF nespravovaná referenční dokumentace rozhraní API)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: a89b29cd459060c93d5ca77bb2154e1a10b02d03
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213646"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="2e038-102">Funkce CreateIDispatchSTAForwarder (WPF nespravovaná referenční dokumentace rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="2e038-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="2e038-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="2e038-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="2e038-104">Používá infrastrukturu Windows Presentation Foundation (WPF) pro správu vlákna a windows.</span><span class="sxs-lookup"><span data-stu-id="2e038-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e038-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e038-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e038-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e038-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="2e038-107">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2e038-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="2e038-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="2e038-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="2e038-109">Ukazatel `IDispatch` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2e038-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="2e038-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="2e038-110">ppForwarder</span></span>  
 <span data-ttu-id="2e038-111">Ukazatel na adresu `IDispatch` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2e038-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e038-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e038-112">Requirements</span></span>  
 <span data-ttu-id="2e038-113">**Platformy:** Zobrazit [rozhraní .NET Framework System Requirements](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e038-113">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 **<span data-ttu-id="2e038-114">KNIHOVNY DLL:</span><span class="sxs-lookup"><span data-stu-id="2e038-114">DLL:</span></span>**  
  
 <span data-ttu-id="2e038-115">V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="2e038-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="2e038-116">V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="2e038-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 **<span data-ttu-id="2e038-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2e038-117">.NET Framework Version:</span></span>** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2e038-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e038-118">See also</span></span>

- [<span data-ttu-id="2e038-119">Referenční informace k nespravovanému rozhraní API WPF</span><span class="sxs-lookup"><span data-stu-id="2e038-119">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
