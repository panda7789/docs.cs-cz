---
title: Aktivovat funkci – referenční informace k rozhraní API nespravovaného WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Activate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: 9c0a235e8b94294ab82da88e43f7446c29739c12
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734512"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="58dbe-102">Activate – funkce (Referenční dokumentace rozhraní API pro nespravované WPF)</span><span class="sxs-lookup"><span data-stu-id="58dbe-102">Activate Function (WPF Unmanaged API Reference)</span></span>

<span data-ttu-id="58dbe-103">Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určeno pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="58dbe-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>

<span data-ttu-id="58dbe-104">Používá se v infrastruktuře Windows Presentation Foundation (WPF) pro správu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="58dbe-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>

## <a name="syntax"></a><span data-ttu-id="58dbe-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58dbe-105">Syntax</span></span>

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a><span data-ttu-id="58dbe-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="58dbe-106">Parameters</span></span>

`pParameters`\
<span data-ttu-id="58dbe-107">Ukazatel na aktivační parametry okna.</span><span class="sxs-lookup"><span data-stu-id="58dbe-107">A pointer to the window's activation parameters.</span></span>

`ppInner`\
<span data-ttu-id="58dbe-108">Ukazatel na adresu vyrovnávací paměti s jedním prvkem, který obsahuje ukazatel na objekt <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>.</span><span class="sxs-lookup"><span data-stu-id="58dbe-108">A pointer to the address of a single-element buffer that contains a pointer to an <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> object.</span></span>

## <a name="requirements"></a><span data-ttu-id="58dbe-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="58dbe-109">Requirements</span></span>

<span data-ttu-id="58dbe-110">**Platformy:** Viz [požadavky na systém .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58dbe-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="58dbe-111">**DLL**</span><span class="sxs-lookup"><span data-stu-id="58dbe-111">**DLL:**</span></span>

<span data-ttu-id="58dbe-112">V .NET Framework 3,0 a 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="58dbe-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>

<span data-ttu-id="58dbe-113">V .NET Framework 4 a novější: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="58dbe-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>

<span data-ttu-id="58dbe-114">**Verze .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58dbe-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="58dbe-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58dbe-115">See also</span></span>

- [<span data-ttu-id="58dbe-116">Odkaz na nespravované rozhraní API subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="58dbe-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
