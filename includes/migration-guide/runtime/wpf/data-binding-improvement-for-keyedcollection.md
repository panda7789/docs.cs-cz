---
ms.openlocfilehash: a0dc2401155a162eaa5aa6b4d9e6af1ca1c2ccc8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802605"
---
### <a name="data-binding-improvement-for-keyedcollection"></a><span data-ttu-id="d18fa-101">Vylepšení vazby dat pro kolekci KeyedCollection</span><span class="sxs-lookup"><span data-stu-id="d18fa-101">Data Binding improvement for KeyedCollection</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d18fa-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d18fa-102">Details</span></span>|<span data-ttu-id="d18fa-103">Oprava <xref:System.Windows.Data.Binding> nesprávné použití indexer IList, pokud zdrojový objekt deklaruje vlastní indexeru se stejným podpisem (třeba kolekci KeyedCollection&lt;int, TItem&gt;).</span><span class="sxs-lookup"><span data-stu-id="d18fa-103">Fixed <xref:System.Windows.Data.Binding> incorrect use of IList indexer when the source object declares a custom indexer with the same signature (e.g. KeyedCollection&lt;int,TItem&gt;).</span></span>|
|<span data-ttu-id="d18fa-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="d18fa-104">Suggestion</span></span>|<span data-ttu-id="d18fa-105">Aby aplikace využívat tuto změnu, musíte spustit na rozhraní .NET Framework 4.7.2 nebo novější, a to musí vyjádřit výslovný souhlas s změnu přidáním následujícího kódu [přepínač AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) k <code>&lt;runtime&gt;</code> oddílu konfiguračního souboru aplikace a nastavení na <code>false</code>:</span><span class="sxs-lookup"><span data-stu-id="d18fa-105">In order for the application to benefit from this change, it must run on the .NET Framework 4.7.2 or later, and it must opt in to the change by adding the following [AppContext switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the <code>&lt;runtime&gt;</code> section of the app config file and setting it to <code>false</code>:</span></span><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="d18fa-106">Scope</span><span class="sxs-lookup"><span data-stu-id="d18fa-106">Scope</span></span>|<span data-ttu-id="d18fa-107">Hlavní</span><span class="sxs-lookup"><span data-stu-id="d18fa-107">Major</span></span>|
|<span data-ttu-id="d18fa-108">Version</span><span class="sxs-lookup"><span data-stu-id="d18fa-108">Version</span></span>|<span data-ttu-id="d18fa-109">4.8</span><span class="sxs-lookup"><span data-stu-id="d18fa-109">4.8</span></span>|
|<span data-ttu-id="d18fa-110">type</span><span class="sxs-lookup"><span data-stu-id="d18fa-110">Type</span></span>|<span data-ttu-id="d18fa-111">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="d18fa-111">Runtime</span></span>|

