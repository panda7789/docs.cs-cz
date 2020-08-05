---
ms.openlocfilehash: c5204e8c80cb737338b053c39083c0cc43786447
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517322"
---
### <a name="binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps"></a>Metody serializace BinaryFormatter jsou zastaralé a zakázané v aplikacích ASP.NET

`Serialize`a `Deserialize` metody <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , a <xref:System.Runtime.Serialization.Formatter> <xref:System.Runtime.Serialization.IFormatter> jsou nyní zastaralé. Kromě toho <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> je serializace ve výchozím nastavení zakázána pro aplikace ASP.NET.

#### <a name="change-description"></a>Popis změny

V důsledku [chyb zabezpečení](../../../../docs/standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) v nástroji <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> jsou nyní zastaralé následující metody. Kromě toho v ASP.NET 5,0 a novějších aplikacích vyvolá <xref:System.NotSupportedException> , pokud webová aplikace nemá opětovné povolení <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> funkcí.

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>

Tyto metody jsou označeny jako zastaralé jako součást snahy o použití <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> v rámci ekosystému .NET.

Následující metody serializace jsou také zastaralé, ale nemají žádné změny v chování:

- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 8

#### <a name="recommended-action"></a>Doporučená akce

- Přestat používat <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve svém kódu. Místo toho zvažte použití <xref:System.Text.Json.JsonSerializer> nebo <xref:System.Xml.Serialization.XmlSerializer> . Další informace najdete v tématu [BinaryFormatter Security Guide](../../../../docs/standard/serialization/binaryformatter-security-guide.md).

- Můžete dočasně potlačit <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> upozornění v době kompilace, což je `SYSLIB0011` . Doporučujeme, abyste před výběrem této možnosti důkladně vyhodnotili kód pro rizika. Nejjednodušší způsob, jak potlačit upozornění, je obklopit jednotlivé weby volání `#pragma` direktiv.

  ```csharp
  // Now read the purchase order back from disk
  using (var readStream = new FileStream("myfile.bin", FileMode.Open))
  {
      var formatter = new BinaryFormatter();
  #pragma warning disable SYSLIB0011
      return (PurchaseOrder)formatter.Deserialize(readStream);
  #pragma warning restore SYSLIB0011
  }
  ```

  Můžete také potlačit upozornění v souboru projektu.

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "BinaryFormatter is obsolete" warnings for entire project -->
    <NoWarn>$(NoWarn);SYSLIB0011</NoWarn>
  </PropertyGroup>
  ```

  Potlačíte-li upozornění v souboru projektu, je upozornění potlačeno pro všechny soubory kódu v projektu. Potlačení SYSLIB0011 potlačí upozornění způsobené použitím jiných zastaralých rozhraní API.

- Chcete-li pokračovat <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> v používání aplikace ASP.NET, můžete je znovu povolit v souboru projektu. Důrazně to však nedoporučujeme. Další informace najdete v tématu [BinaryFormatter Security Guide](../../../../docs/standard/serialization/binaryformatter-security-guide.md).

  ```xml
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Warning: Setting the following switch is *NOT* recommended in web apps. -->
    <EnableUnsafeBinaryFormatterSerialization>true</EnableUnsafeBinaryFormatterSerialization>
  </PropertyGroup>
  ```

Další informace o doporučených akcích najdete v tématu [řešení chyb BinaryFormatter obsoletion a deaktivace](https://aka.ms/binaryformatter).

#### <a name="category"></a>Kategorie

- Knihovny Core .NET
- ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize`
- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`
- `M:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)`

-->
