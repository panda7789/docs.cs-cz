---
title: LoadFromHistory Function - WPF nespravované rozhraní API odkaz
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: be9b8658614e678b4370044a753554859d230fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141572"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="7f4fb-102">Funkce LoadFromHistory (WPF Unmanaged API Reference)</span><span class="sxs-lookup"><span data-stu-id="7f4fb-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="7f4fb-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určeno k použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="7f4fb-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="7f4fb-104">Používá infrastrukturu WPF (Windows Presentation Foundation) pro správu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7f4fb-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f4fb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f4fb-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f4fb-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f4fb-106">Parameters</span></span>  
 <span data-ttu-id="7f4fb-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="7f4fb-107">pHistoryStream</span></span>  
 <span data-ttu-id="7f4fb-108">Ukazatel na datový proud informací o historii.</span><span class="sxs-lookup"><span data-stu-id="7f4fb-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="7f4fb-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="7f4fb-109">pBindCtx</span></span>  
 <span data-ttu-id="7f4fb-110">Ukazatel na kontext vazby.</span><span class="sxs-lookup"><span data-stu-id="7f4fb-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f4fb-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f4fb-111">Requirements</span></span>  
 <span data-ttu-id="7f4fb-112">**Platformy:** Viz [Požadavky na systém rozhraní .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f4fb-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f4fb-113">**Knihovny dll:**</span><span class="sxs-lookup"><span data-stu-id="7f4fb-113">**DLL:**</span></span>  
  
 <span data-ttu-id="7f4fb-114">V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll ll</span><span class="sxs-lookup"><span data-stu-id="7f4fb-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="7f4fb-115">V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="7f4fb-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="7f4fb-116">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f4fb-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f4fb-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f4fb-117">See also</span></span>

- [<span data-ttu-id="7f4fb-118">Referenční informace k nespravovanému rozhraní API WPF</span><span class="sxs-lookup"><span data-stu-id="7f4fb-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
