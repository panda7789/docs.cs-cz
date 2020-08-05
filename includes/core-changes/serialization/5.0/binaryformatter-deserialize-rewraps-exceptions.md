---
ms.openlocfilehash: 4aef35502fc93cbf0399e3c8d0932338829d6c07
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517347"
---
### <a name="binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception"></a>BinaryFormatter. deserializace přebalí některé výjimky v SerializationException.

<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>Metoda teď znovu zabalí některé objekty výjimek uvnitř a <xref:System.Runtime.Serialization.SerializationException> před tím, než se výjimka rozšíří zpět volajícímu.

#### <a name="change-description"></a>Popis změny

Dřív <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> Metoda povolila nějaké libovolné výjimky, například <xref:System.ArgumentNullException> , k rozšíření zásobníku na jeho volající.

V rozhraní .NET 5,0 a novějších <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> metod metoda lépe zachycuje výjimky, ke kterým dochází v důsledku neplatných operací deserializace a zabalí je do <xref:System.Runtime.Serialization.SerializationException> .

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 1

#### <a name="recommended-action"></a>Doporučená akce

Ve většině případů není nutné provádět žádnou akci. Nicméně pokud váš web volání závisí na vyvolání konkrétní výjimky, můžete zrušit zabalení výjimky z vnější <xref:System.Runtime.Serialization.SerializationException> , jak je znázorněno v následujícím příkladu.

```csharp
Stream inputStream = GetInputStream();
var formatter = new BinaryFormatter();

try
{
    object deserialized = formatter.Deserialize(inputStream);
}
catch (MyException myEx)
{
    // Handle 'myEx' here in case it was thrown directly.
}
catch (SerializationException serEx)
{
    if (serEx.InnerException is MyException myEx)
    {
        // Handle 'myEx' here in case it was wrapped in SerializationException.
    }
    else
    {
        throw;
    }
}
```

#### <a name="category"></a>Kategorie

Serializace

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`

-->
