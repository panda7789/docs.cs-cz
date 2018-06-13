---
title: Funkce CreateIDispatchSTAForwarder (WPF nespravované rozhraní API)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: f7e45d5cafa40ba147fe39888e74a67ac9f95c5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536648"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="427b3-102">Funkce CreateIDispatchSTAForwarder (WPF nespravované rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="427b3-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="427b3-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="427b3-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="427b3-104">Používá infrastrukturu Windows Presentation Foundation (WPF) pro přístup z více vláken a windows management.</span><span class="sxs-lookup"><span data-stu-id="427b3-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="427b3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="427b3-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="427b3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="427b3-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="427b3-107">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="427b3-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="427b3-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="427b3-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="427b3-109">Ukazatel na `IDispatch` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="427b3-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="427b3-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="427b3-110">ppForwarder</span></span>  
 <span data-ttu-id="427b3-111">Ukazatel na adresu `IDispatch` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="427b3-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="427b3-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="427b3-112">Requirements</span></span>  
 <span data-ttu-id="427b3-113">**Platformy:** najdete v části [požadavky na systém rozhraní .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="427b3-113">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="427b3-114">**KNIHOVNY DLL:**</span><span class="sxs-lookup"><span data-stu-id="427b3-114">**DLL:**</span></span>  
  
 <span data-ttu-id="427b3-115">V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="427b3-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="427b3-116">V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="427b3-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="427b3-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="427b3-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="427b3-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="427b3-118">See Also</span></span>  
 [<span data-ttu-id="427b3-119">Odkaz na nespravované rozhraní API subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="427b3-119">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
