---
title: Aktivovat funkci (WPF nespravovaná referenční dokumentace rozhraní API)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Activate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: ee231653815bd5ef75d58979034e3b3be9f5ba54
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480777"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="01c69-102">Aktivovat funkci (WPF nespravovaná referenční dokumentace rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="01c69-102">Activate Function (WPF Unmanaged API Reference)</span></span>

<span data-ttu-id="01c69-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="01c69-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>

<span data-ttu-id="01c69-104">Používá infrastrukturu Windows Presentation Foundation (WPF) pro správu systému windows.</span><span class="sxs-lookup"><span data-stu-id="01c69-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>

## <a name="syntax"></a><span data-ttu-id="01c69-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01c69-105">Syntax</span></span>

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a><span data-ttu-id="01c69-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="01c69-106">Parameters</span></span>

`pParameters`\
<span data-ttu-id="01c69-107">Ukazatel na parametry v okně aktivace.</span><span class="sxs-lookup"><span data-stu-id="01c69-107">A pointer to the window's activation parameters.</span></span>

`ppInner`\
<span data-ttu-id="01c69-108">Adresa vyrovnávací paměti jedním prvkem, který obsahuje ukazatel na ukazatel <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="01c69-108">A pointer to the address of a single-element buffer that contains a pointer to an <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> object.</span></span>

## <a name="requirements"></a><span data-ttu-id="01c69-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01c69-109">Requirements</span></span>

<span data-ttu-id="01c69-110">**Platformy:** Zobrazit [rozhraní .NET Framework System Requirements](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01c69-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="01c69-111">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="01c69-111">**DLL:**</span></span>

<span data-ttu-id="01c69-112">V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="01c69-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>

<span data-ttu-id="01c69-113">V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="01c69-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>

<span data-ttu-id="01c69-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01c69-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="01c69-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01c69-115">See also</span></span>

- [<span data-ttu-id="01c69-116">Odkaz na nespravované rozhraní API subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="01c69-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
