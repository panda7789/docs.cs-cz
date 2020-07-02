---
ms.openlocfilehash: beb869208e8d48d762d94b5989a558fa2f1aaf29
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622008"
---
### <a name="data-binding-improvement-for-keyedcollection"></a>Vylepšení datových vazeb pro KeyedCollection

#### <a name="details"></a>Podrobnosti

Opravili jsme <xref:System.Windows.Data.Binding> nesprávné použití indexeru IList, pokud zdrojový objekt deklaruje vlastní indexer se stejnou signaturou (například KeyedCollection &lt; int, TItem &gt; ).

#### <a name="suggestion"></a>Návrh

Aby aplikace, která cílí na starší verzi, mohla využít tuto změnu, musí běžet v .NET Framework 4,8 nebo novějším a musí se ke změně přihlásit přidáním následujícího [přepínače AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) do <code>&lt;runtime&gt;</code> části konfiguračního souboru aplikace a jeho nastavením na <code>false</code> :<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Hlavní|
|Verze|4,8|
|Typ|Modul runtime|
