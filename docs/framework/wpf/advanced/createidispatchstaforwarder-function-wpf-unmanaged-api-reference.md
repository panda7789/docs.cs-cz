---
title: Funkce CreateIDispatchSTAForwarder – nespravovaný odkaz rozhraní API WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: e151ffa6eb5f1dc7479c699e0d7f9f3f57833ebd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174716"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="efd37-102">Funkce CreateIDispatchSTAForwarder (WPF Unmanaged API Reference)</span><span class="sxs-lookup"><span data-stu-id="efd37-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="efd37-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určeno k použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="efd37-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="efd37-104">Používá infrastrukturu WPF (Windows Presentation Foundation) pro správu vláken a systému Windows.</span><span class="sxs-lookup"><span data-stu-id="efd37-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efd37-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efd37-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="efd37-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="efd37-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="efd37-107">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="efd37-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="efd37-108">pDelegát odeslání</span><span class="sxs-lookup"><span data-stu-id="efd37-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="efd37-109">Ukazatel na `IDispatch` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="efd37-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="efd37-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="efd37-110">ppForwarder</span></span>  
 <span data-ttu-id="efd37-111">Ukazatel na adresu `IDispatch` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="efd37-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efd37-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="efd37-112">Requirements</span></span>  
 <span data-ttu-id="efd37-113">**Platformy:** Viz [Požadavky na systém rozhraní .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efd37-113">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efd37-114">**Knihovny dll:**</span><span class="sxs-lookup"><span data-stu-id="efd37-114">**DLL:**</span></span>  
  
 <span data-ttu-id="efd37-115">V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll ll</span><span class="sxs-lookup"><span data-stu-id="efd37-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="efd37-116">V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="efd37-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="efd37-117">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efd37-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efd37-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="efd37-118">See also</span></span>

- [<span data-ttu-id="efd37-119">Referenční informace k nespravovanému rozhraní API WPF</span><span class="sxs-lookup"><span data-stu-id="efd37-119">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
