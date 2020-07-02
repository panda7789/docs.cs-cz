---
ms.openlocfilehash: 483902ff2ec54d58bfb00dd8ee7fd78868f70ab4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620047"
---
### <a name="binaryformatter-can-fail-to-find-type-from-loadfrom-context"></a>BinaryFormatter nemůže najít typ z kontextu LoadFrom.

#### <a name="details"></a>Podrobnosti

Od .NET Framework 4,5 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> může několik změn způsobit rozdíly v deserializaci při použití <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> k deserializaci typů, které byly načteny v kontextu LoadFrom. Tyto změny jsou způsobeny tím, že nové způsoby <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> nyní načtou typ, který při <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> pokusu o deserializaci na tento typ způsobí jiné chování. Výchozí serializace pořadač automaticky nehledá kontext LoadFrom, i když v některých případech mohl být v závislosti na starém chování objektu XmlSerializer zpracován. Z důvodu změn platí, že při načítání typu ze sestavení načteného v jiném kontextu <xref:System.IO.FileNotFoundException?displayProperty=fullName> může být vyvolána výjimka.

#### <a name="suggestion"></a>Návrh

Pokud se tato výjimka zobrazuje, <code>Binder</code> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> může být vlastnost nastavená na vlastní pořadač, který bude najít správný typ.<pre><code class="lang-csharp">var formatter = new BinaryFormatter { Binder = new TypeFinderBinder() }&#13;&#10;</code></pre>A pak vlastní pořadač:<pre><code class="lang-csharp">public class TypeFinderBinder : SerializationBinder&#13;&#10;{&#13;&#10;private static readonly string s_assemblyName = Assembly.GetExecutingAssembly().FullName;&#13;&#10;&#13;&#10;public override Type BindToType(string assemblyName, string typeName)&#13;&#10;{&#13;&#10;return Type.GetType(String.Format(CultureInfo.InvariantCulture, &quot;{0}, {1}&quot;, typeName, s_assemblyName));&#13;&#10;}&#13;&#10;}&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|
