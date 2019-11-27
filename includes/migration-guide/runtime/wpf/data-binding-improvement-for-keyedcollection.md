---
ms.openlocfilehash: 8aae403e3f23d3bfc755140b2ac29d757f10f753
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451615"
---
### <a name="data-binding-improvement-for-keyedcollection"></a>Vylepšení datových vazeb pro KeyedCollection

|   |   |
|---|---|
|Podrobnosti|Opraveno <xref:System.Windows.Data.Binding> nesprávné použití indexeru IList, pokud zdrojový objekt deklaruje vlastní indexer se stejnou signaturou (například KeyedCollection&lt;int, TItem&gt;).|
|Doporučení|Aby aplikace, která cílí na starší verzi, mohla využít tuto změnu, musí běžet v .NET Framework 4,8 nebo novějším a musí se ke změně přihlásit přidáním následujícího [přepínače AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) do <code>&lt;runtime&gt;</code> oddílu konfiguračního souboru aplikace a jeho nastavením na <code>false</code>:<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Obor|Závažná|
|Version|4.8|
|Typ|Runtime|
