---
ms.openlocfilehash: e66a5c2a33a4ab5cf35013c1843936ffd01f90a2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614501"
---
### <a name="serialport-background-thread-exceptions"></a>Portu SerialPort výjimky vlákna na pozadí

#### <a name="details"></a>Podrobnosti

Vlákna na pozadí vytvořená pomocí <xref:System.IO.Ports.SerialPort> datových proudů už neukončí proces, když jsou vyvolány výjimky operačního systému. <br/>V aplikacích, které cílí na .NET Framework 4,7 a starších verzí, je proces ukončen, pokud je vyvolána výjimka operačního systému ve vlákně na pozadí vytvořeném pomocí <xref:System.IO.Ports.SerialPort> datového proudu. <br/>V aplikacích, které cílí na .NET Framework 4.7.1 nebo novější verzi, vlákna na pozadí čekají na události operačního systému související s aktivním sériovým portem a v některých případech by mohlo dojít k chybě, jako je například náhlé odebrání sériového portu.

#### <a name="suggestion"></a>Návrh

U aplikací, které cílí na .NET Framework 4.7.1, se můžete rozhodnout o zpracování výjimek, pokud to není žádoucí, a to tak, že do `<runtime>` části souboru přidáte následující `app.config` :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true" />
</runtime>
```

Pro aplikace, které jsou cíleny na starší verze .NET Framework, ale běží na .NET Framework 4.7.1 nebo novější, můžete vyjádřit ke zpracování výjimek přidáním následujícího do `<runtime>` části `app.config` souboru:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false" />
</runtime>
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.7.1       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
