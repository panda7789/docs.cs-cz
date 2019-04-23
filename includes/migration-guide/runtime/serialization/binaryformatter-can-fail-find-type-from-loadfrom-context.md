---
ms.openlocfilehash: ac929a8b3e9a7d56122f5699c51819ad483d1f5e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803695"
---
### <a name="binaryformatter-can-fail-to-find-type-from-loadfrom-context"></a>BinaryFormatter může selhat se najít typ kontext LoadFrom je přepnut

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.5, řadu <xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> změny můžou způsobit rozdíly v deserializaci při použití <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> k deserializaci typy, které kdyby byly načteny v kontextu LoadFrom. Tyto změny jsou způsobeny nové způsoby <xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> se teď načte typ, který způsobí, že různé chování při <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> pokusí rekonstruovat do typu později. Výchozí vazač serializace neprohledává automaticky kontext LoadFrom, i když může fungovat v některých případech na základě staré chování XmlSerializer. Z důvodu změn, při načítání typu ze sestavení načíst v jiném kontextu <xref:System.IO.FileNotFoundException?displayProperty=name> může být vyvolána.|
|Doporučení|Pokud tuto výjimku je vidět, <code>Binder</code> vlastnost <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> lze nastavit na vlastní vázací objekt, který vyhledá správný typ.<pre><code class="lang-csharp">var formatter = new BinaryFormatter { Binder = new TypeFinderBinder() }&#13;&#10;</code></pre>A pak vlastní vázací objekt:<pre><code class="lang-csharp">public class TypeFinderBinder : SerializationBinder&#13;&#10;{&#13;&#10;private static readonly string s_assemblyName = Assembly.GetExecutingAssembly().FullName;&#13;&#10;&#13;&#10;public override Type BindToType(string assemblyName, string typeName)&#13;&#10;{&#13;&#10;return Type.GetType(String.Format(CultureInfo.InvariantCulture, &quot;{0}, {1}&quot;, typeName, s_assemblyName));&#13;&#10;}&#13;&#10;}&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|
