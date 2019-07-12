---
ms.openlocfilehash: a0dc2401155a162eaa5aa6b4d9e6af1ca1c2ccc8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802605"
---
### <a name="data-binding-improvement-for-keyedcollection"></a>Vylepšení vazby dat pro kolekci KeyedCollection

|   |   |
|---|---|
|Podrobnosti|Oprava <xref:System.Windows.Data.Binding> nesprávné použití indexer IList, pokud zdrojový objekt deklaruje vlastní indexeru se stejným podpisem (třeba kolekci KeyedCollection&lt;int, TItem&gt;).|
|Doporučení|Aby aplikace využívat tuto změnu, musíte spustit na rozhraní .NET Framework 4.7.2 nebo novější, a to musí vyjádřit výslovný souhlas s změnu přidáním následujícího kódu [přepínač AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) k <code>&lt;runtime&gt;</code> oddílu konfiguračního souboru aplikace a nastavení na <code>false</code>:<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Scope|Hlavní|
|Version|4.8|
|type|Modul runtime|

