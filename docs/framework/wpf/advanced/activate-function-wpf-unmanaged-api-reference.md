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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777166"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a>Aktivovat funkci (WPF nespravovaná referenční dokumentace rozhraní API)

Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo v kódu.

Používá infrastrukturu Windows Presentation Foundation (WPF) pro správu systému windows.

## <a name="syntax"></a>Syntaxe

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a>Parametry

`pParameters`\
Ukazatel na parametry v okně aktivace.

`ppInner`\
Adresa vyrovnávací paměti jedním prvkem, který obsahuje ukazatel na ukazatel <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> objektu.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [rozhraní .NET Framework System Requirements](../../get-started/system-requirements.md).

**DLL:**

V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll

V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll

**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]

## <a name="see-also"></a>Viz také:

- [Odkaz na nespravované rozhraní API subsystému WPF](wpf-unmanaged-api-reference.md)
