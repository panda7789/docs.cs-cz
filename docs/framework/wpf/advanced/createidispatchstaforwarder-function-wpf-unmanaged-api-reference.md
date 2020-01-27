---
title: Funkce CreateIDispatchSTAForwarder – reference nespravovaného rozhraní API WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: 67f2542733fb9c6af197c99ede2bd097ce876b5d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738031"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="e7fe3-102">CreateIDispatchSTAForwarder – funkce (Referenční dokumentace rozhraní API nespravovaného subsystému WPF)</span><span class="sxs-lookup"><span data-stu-id="e7fe3-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="e7fe3-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určeno pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="e7fe3-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="e7fe3-104">Používáno infrastrukturou Windows Presentation Foundation (WPF) pro vlákna a správu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e7fe3-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7fe3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7fe3-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7fe3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7fe3-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="e7fe3-107">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e7fe3-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="e7fe3-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="e7fe3-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="e7fe3-109">Ukazatel na rozhraní `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="e7fe3-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="e7fe3-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="e7fe3-110">ppForwarder</span></span>  
 <span data-ttu-id="e7fe3-111">Ukazatel na adresu `IDispatch`ho rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e7fe3-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7fe3-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7fe3-112">Requirements</span></span>  
 <span data-ttu-id="e7fe3-113">**Platformy:** Viz [požadavky na systém .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7fe3-113">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7fe3-114">**DLL**</span><span class="sxs-lookup"><span data-stu-id="e7fe3-114">**DLL:**</span></span>  
  
 <span data-ttu-id="e7fe3-115">V .NET Framework 3,0 a 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="e7fe3-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="e7fe3-116">V .NET Framework 4 a novější: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="e7fe3-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="e7fe3-117">**Verze .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7fe3-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7fe3-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7fe3-118">See also</span></span>

- [<span data-ttu-id="e7fe3-119">Odkaz na nespravované rozhraní API subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="e7fe3-119">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
