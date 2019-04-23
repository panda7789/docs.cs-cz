---
ms.openlocfilehash: 50d251d8e8ec28fa8a895f1ef66f7efc1657eff4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982247"
---
### <a name="data-binding-improvement-for-keyedcollection"></a>Vylepšení vazby dat pro kolekci KeyedCollection

|   |   |
|---|---|
|Podrobnosti|Oprava <xref:System.Windows.Data.Binding> nesprávné použití indexer IList, pokud zdrojový objekt deklaruje vlastní indexeru se stejným podpisem (třeba kolekci KeyedCollection&lt;int, TItem&gt;).|
|Doporučení|Aby aplikace využívat tuto změnu, musíte spustit na rozhraní .NET Framework 4.7.2 nebo novější, a to musí vyjádřit výslovný souhlas s změnu přidáním následujícího kódu [přepínač AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) k <code>&lt;runtime&gt;</code> oddílu konfiguračního souboru aplikace a nastavení na <code>false</code>:<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Hlavní|
|Version|4.8|
|Type|Modul runtime|
