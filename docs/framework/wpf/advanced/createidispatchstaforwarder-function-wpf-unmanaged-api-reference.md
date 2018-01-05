---
title: "Funkce CreateIDispatchSTAForwarder (WPF nespravované rozhraní API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: CreateIDispatchSTAForwarder
api_location: PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5139784fdc067c09d032c0bf37114e0eb1caac33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="90b18-102">Funkce CreateIDispatchSTAForwarder (WPF nespravované rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="90b18-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="90b18-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="90b18-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="90b18-104">Používá infrastrukturu Windows Presentation Foundation (WPF) pro přístup z více vláken a windows management.</span><span class="sxs-lookup"><span data-stu-id="90b18-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90b18-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90b18-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90b18-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="90b18-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="90b18-107">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="90b18-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="90b18-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="90b18-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="90b18-109">Ukazatel na `IDispatch` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="90b18-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="90b18-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="90b18-110">ppForwarder</span></span>  
 <span data-ttu-id="90b18-111">Ukazatel na adresu `IDispatch` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="90b18-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90b18-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90b18-112">Requirements</span></span>  
 <span data-ttu-id="90b18-113">**Platformy:** najdete v části [požadavky na systém rozhraní .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90b18-113">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90b18-114">**KNIHOVNY DLL:**</span><span class="sxs-lookup"><span data-stu-id="90b18-114">**DLL:**</span></span>  
  
 <span data-ttu-id="90b18-115">V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="90b18-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="90b18-116">V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="90b18-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="90b18-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90b18-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90b18-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="90b18-118">See Also</span></span>  
 [<span data-ttu-id="90b18-119">Odkaz na nespravované rozhraní API subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="90b18-119">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
