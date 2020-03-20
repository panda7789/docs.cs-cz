---
ms.openlocfilehash: 8aae403e3f23d3bfc755140b2ac29d757f10f753
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74451615"
---
### <a name="data-binding-improvement-for-keyedcollection"></a>Vylepšení datové vazby pro KeyedCollection

|   |   |
|---|---|
|Podrobnosti|Opraveno <xref:System.Windows.Data.Binding> nesprávné použití indexeru IList, když zdrojový objekt deklaruje vlastní&lt;indexer se&gt;stejným podpisem (například KeyedCollection int,TItem).|
|Návrh|Aby aplikace, která cílí na starší verzi, aby mohla těžit z této změny, musí být spuštěna v rozhraní .NET Framework 4.8 nebo novějším a musí <code>false</code>se ke změně přihlásit přidáním následujícího [přepínače AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) do <code>&lt;runtime&gt;</code> části konfiguračního souboru aplikace a nastavením na :<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Hlavní|
|Version|4.8|
|Typ|Modul runtime|
