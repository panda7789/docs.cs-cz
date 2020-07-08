---
title: QuotedPairReader – třída (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mail.QuotedPairReader
- System.Net.Mail.QuotedPairReader.CountQuotedChars
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 898c6e9d2d5dd02f3d5f9c096ad470b5dd445d1d
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051308"
---
# <a name="quotedpairreader-class"></a>QuotedPairReader – třída

Určuje, které znaky jsou v řetězci v uvozovkách v uvozovkách (uvozené pomocí řídicích znaků). Tuto třídu nelze zdědit.

```csharp
internal static class QuotedPairReader
```

> [!WARNING]
> Tato třída je interní a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.

## <a name="countquotedchars-method"></a>Metoda CountQuotedChars

Spočítá počet po sobě jdoucích znaků v uvozovkách, včetně několika předchozích zpětných lomítek v zadaném řetězci. Například při `a\\\b` zadání řetězce a indexu objektu se `4` Metoda vrátí `4` , protože `b` je v uvozovkách a tedy tři předchozí zpětná lomítka.

```csharp
internal static int CountQuotedChars(string data, int index, bool permitUnicodeEscaping)
```

### <a name="parameters"></a>Parametry

- `data` <xref:System.String>

  Datový řetězec, ve kterém se mají počítat po sobě jdoucí znaky v uvozovkách

- `index` <xref:System.Int32>

  Pozice v zadaném řetězci až do a včetně, které by měly být započítány po sobě jdoucí uvozovky.

- `permitUnicodeEscaping` <xref:System.Boolean>

  `true`povolení řídicích znaků znaků Unicode; v opačném případě `false` .

### <a name="return-value"></a>Vrácená hodnota

<xref:System.Int32?displayProperty=nameWithType>

`0`Pokud znak na zadaném indexu není uvozen řídicím znakem; v opačném případě počet po sobě jdoucích znaků v uvozovkách až do a včetně znaku na `index` .

### <a name="exceptions"></a>Výjimky

<xref:System.FormatException?displayProperty=nameWithType>

Byl nalezen řídicí znak Unicode, který však není povolen.

## <a name="requirements"></a>Požadavky

**Obor názvů:**<xref:System.Net>

**Sestavení:** Systém (v System.dll)
