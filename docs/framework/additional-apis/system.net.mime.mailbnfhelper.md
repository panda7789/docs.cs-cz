---
title: MailBnfHelper – třída (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mime.MailBnfHelper
- System.Net.Mime.MailBnfHelper.Ascii7bitMaxValue
- System.Net.Mime.MailBnfHelper.Atext
- System.Net.Mime.MailBnfHelper.CR
- System.Net.Mime.MailBnfHelper.Ctext
- System.Net.Mime.MailBnfHelper.Dot
- System.Net.Mime.MailBnfHelper.EndComment
- System.Net.Mime.MailBnfHelper.LF
- System.Net.Mime.MailBnfHelper.Space
- System.Net.Mime.MailBnfHelper.StartComment
- System.Net.Mime.MailBnfHelper.Tab
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 86c98726a7886285917b6be8c7631ca1e9e425e6
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990328"
---
# <a name="mailbnfhelper-class"></a>MailBnfHelper – třída

Obsahuje metody nástrojů pro analýzu řetězců ve formátu internetových zpráv. Tuto třídu nelze zdědit.

```csharp
internal static class MailBnfHelper
```

> [!WARNING]
> Tato třída je interní a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.

## <a name="ascii7bitmaxvalue-field"></a>Pole Ascii7bitMaxValue

Představuje maximální hodnotu 7 bitů ASCII.

```csharp
internal static readonly int Ascii7bitMaxValue
```

## <a name="atext-field"></a>Pole atext

Představuje znaky povolené ve atomech.

```csharp
internal static bool[] Atext
```

## <a name="cr-field"></a>Pole CR

Představuje znak návratu na začátek řádku.

```csharp
internal static readonly char CR
```

## <a name="ctext-field"></a>Pole CTEXT

Představuje znaky povolené v komentářích.

```csharp
internal static bool[] Ctext
```

## <a name="dot-field"></a>Pole s tečkou

Představuje znak úplného zastavení ( `.` ).

```csharp
internal static readonly char Dot
```

## <a name="endcomment-field"></a>Pole EndComment

Představuje znak, který určuje konec komentáře.

```csharp
internal static readonly char EndComment
```

## <a name="lf-field"></a>Pole LF

Představuje znak kanálu čáry.

```csharp
internal static readonly char LF
```

## <a name="space-field"></a>Pole prostor

Představuje znak mezery.

```csharp
internal static readonly char Space
```

## <a name="startcomment-field"></a>Pole StartComment

Představuje znak, který určuje začátek komentáře.

```csharp
internal static readonly char StartComment
```

## <a name="tab-field"></a>Pole karty

Představuje znak tabulátoru.

```csharp
internal static readonly char Tab
```

## <a name="requirements"></a>Požadavky

**Obor názvů:**<xref:System.Net>

**Sestavení:** Systém (v System.dll)
