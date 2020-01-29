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
# <a name="activate-function-wpf-unmanaged-api-reference"></a>Activate – funkce (Referenční dokumentace rozhraní API pro nespravované WPF)

Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určeno pro použití přímo v kódu.

Používá se v infrastruktuře Windows Presentation Foundation (WPF) pro správu systému Windows.

## <a name="syntax"></a>Syntaxe

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a>Parametry

`pParameters`\
Ukazatel na aktivační parametry okna.

`ppInner`\
Ukazatel na adresu vyrovnávací paměti s jedním prvkem, který obsahuje ukazatel na objekt <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém .NET Framework](../../get-started/system-requirements.md).

**DLL**

V .NET Framework 3,0 a 3,5: PresentationHostDLL. dll

V .NET Framework 4 a novější: PresentationHost_v0400. dll

**Verze .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]

## <a name="see-also"></a>Viz také:

- [Odkaz na nespravované rozhraní API subsystému WPF](wpf-unmanaged-api-reference.md)
