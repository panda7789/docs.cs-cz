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
ms.openlocfilehash: c4da322bf779e084f12529d0da6949ef6ada5cf3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379650"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="dcebd-102">Funkce CreateIDispatchSTAForwarder (WPF nespravovaná referenční dokumentace rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="dcebd-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="dcebd-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="dcebd-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="dcebd-104">Používá infrastrukturu Windows Presentation Foundation (WPF) pro správu vlákna a windows.</span><span class="sxs-lookup"><span data-stu-id="dcebd-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcebd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcebd-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dcebd-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dcebd-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="dcebd-107">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dcebd-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="dcebd-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="dcebd-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="dcebd-109">Ukazatel `IDispatch` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dcebd-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="dcebd-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="dcebd-110">ppForwarder</span></span>  
 <span data-ttu-id="dcebd-111">Ukazatel na adresu `IDispatch` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dcebd-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcebd-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dcebd-112">Requirements</span></span>  
 <span data-ttu-id="dcebd-113">**Platformy:** Zobrazit [rozhraní .NET Framework System Requirements](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcebd-113">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcebd-114">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="dcebd-114">**DLL:**</span></span>  
  
 <span data-ttu-id="dcebd-115">V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="dcebd-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="dcebd-116">V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="dcebd-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="dcebd-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcebd-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcebd-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dcebd-118">See also</span></span>
- [<span data-ttu-id="dcebd-119">Odkaz na nespravované rozhraní API subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="dcebd-119">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
