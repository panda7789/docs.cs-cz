---
title: Aktivovat funkci (WPF nespravovaná referenční dokumentace rozhraní API)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Acrivate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: 4e79b74dc8bb7d57125c27e17e8f52d607fffcf1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721950"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="c434d-102">Aktivovat funkci (WPF nespravovaná referenční dokumentace rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="c434d-102">Activate Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="c434d-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="c434d-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="c434d-104">Používá infrastrukturu Windows Presentation Foundation (WPF) pro správu systému windows.</span><span class="sxs-lookup"><span data-stu-id="c434d-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c434d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c434d-105">Syntax</span></span>  
  
```cpp  
void Activate(  
    const ActivateParameters* pParameters,  
    __deref_out_ecount(1) LPUNKNOWN* ppInner,  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c434d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c434d-106">Parameters</span></span>  
 <span data-ttu-id="c434d-107">pParameters</span><span class="sxs-lookup"><span data-stu-id="c434d-107">pParameters</span></span>  
 <span data-ttu-id="c434d-108">Ukazatel na parametry v okně aktivace.</span><span class="sxs-lookup"><span data-stu-id="c434d-108">A pointer to the window's activation parameters.</span></span>  
  
 <span data-ttu-id="c434d-109">ppInner</span><span class="sxs-lookup"><span data-stu-id="c434d-109">ppInner</span></span>  
 <span data-ttu-id="c434d-110">Adresa vyrovnávací paměti jedním prvkem, který obsahuje ukazatel na ukazatel <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="c434d-110">A pointer to the address of a single-element buffer that contains a pointer to an <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c434d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c434d-111">Requirements</span></span>  
 <span data-ttu-id="c434d-112">**Platformy:** Zobrazit [rozhraní .NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c434d-112">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c434d-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="c434d-113">**DLL:**</span></span>  
  
 <span data-ttu-id="c434d-114">V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="c434d-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="c434d-115">V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="c434d-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="c434d-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c434d-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c434d-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c434d-117">See also</span></span>
- [<span data-ttu-id="c434d-118">Odkaz na nespravované rozhraní API subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="c434d-118">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
