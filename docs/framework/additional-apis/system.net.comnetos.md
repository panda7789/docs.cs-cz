---
title: ComNetOS – třída (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ComNetOS
- System.Net.ComNetOS.IsWin7orLater
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ed2b970d07df2c338870b386e75c1688703f1d68
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990342"
---
# <a name="comnetos-class"></a>ComNetOS – třída

Poskytuje informace o aktuálním operačním systému, jako je jeho verze a typ instalace (klient nebo Server). Tuto třídu nelze zdědit.
  
```csharp  
internal static class ComNetOS
```

> [!WARNING]
> Tato třída je interní a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.

## <a name="iswin7orlater-field"></a>Pole IsWin7orLater

Určuje, jestli je verze operačního systému Windows 7 nebo novější.

```csharp
internal static readonly bool IsWin7orLater
```

## <a name="requirements"></a>Požadavky

**Obor názvů:**<xref:System.Net>

**Sestavení:** Systém (v System.dll)
