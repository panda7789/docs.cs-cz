---
ms.openlocfilehash: beb869208e8d48d762d94b5989a558fa2f1aaf29
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622008"
---
### <a name="data-binding-improvement-for-keyedcollection"></a><span data-ttu-id="7b82a-101">Vylepšení datových vazeb pro KeyedCollection</span><span class="sxs-lookup"><span data-stu-id="7b82a-101">Data Binding improvement for KeyedCollection</span></span>

#### <a name="details"></a><span data-ttu-id="7b82a-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="7b82a-102">Details</span></span>

<span data-ttu-id="7b82a-103">Opravili jsme <xref:System.Windows.Data.Binding> nesprávné použití indexeru IList, pokud zdrojový objekt deklaruje vlastní indexer se stejnou signaturou (například KeyedCollection &lt; int, TItem &gt; ).</span><span class="sxs-lookup"><span data-stu-id="7b82a-103">Fixed <xref:System.Windows.Data.Binding> incorrect use of IList indexer when the source object declares a custom indexer with the same signature (for example, KeyedCollection&lt;int,TItem&gt;).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7b82a-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="7b82a-104">Suggestion</span></span>

<span data-ttu-id="7b82a-105">Aby aplikace, která cílí na starší verzi, mohla využít tuto změnu, musí běžet v .NET Framework 4,8 nebo novějším a musí se ke změně přihlásit přidáním následujícího [přepínače AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) do <code>&lt;runtime&gt;</code> části konfiguračního souboru aplikace a jeho nastavením na <code>false</code> :</span><span class="sxs-lookup"><span data-stu-id="7b82a-105">In order for an application that targets an older version to benefit from this change, it must run on the .NET Framework 4.8 or later, and it must opt in to the change by adding the following [AppContext switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the <code>&lt;runtime&gt;</code> section of the app config file and setting it to <code>false</code>:</span></span><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="7b82a-106">Name</span><span class="sxs-lookup"><span data-stu-id="7b82a-106">Name</span></span>    | <span data-ttu-id="7b82a-107">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7b82a-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7b82a-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="7b82a-108">Scope</span></span>   |<span data-ttu-id="7b82a-109">Hlavní</span><span class="sxs-lookup"><span data-stu-id="7b82a-109">Major</span></span>|
|<span data-ttu-id="7b82a-110">Verze</span><span class="sxs-lookup"><span data-stu-id="7b82a-110">Version</span></span>|<span data-ttu-id="7b82a-111">4,8</span><span class="sxs-lookup"><span data-stu-id="7b82a-111">4.8</span></span>|
|<span data-ttu-id="7b82a-112">Typ</span><span class="sxs-lookup"><span data-stu-id="7b82a-112">Type</span></span>|<span data-ttu-id="7b82a-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="7b82a-113">Runtime</span></span>|
