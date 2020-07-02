---
ms.openlocfilehash: 4303b177ffe01328965c909a5a3809414fcead91
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614596"
---
### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a>Výchozí algoritmus hash pro kompilátor značek WPF je nyní SHA256

#### <a name="details"></a>Podrobnosti

WPF MarkupCompiler poskytuje kompilační služby pro soubory značek XAML.  V .NET Framework 4.7.1 a starších verzích byl výchozí algoritmus hash použitý pro kontrolní součty SHA1. Vzhledem k nedávnému vlivu zabezpečení na SHA1 se tato výchozí hodnota změnila na SHA256 počínaje 4.7.2em .NET Framework.  Tato změna má vliv na veškerou generaci kontrolního součtu pro soubory značek během kompilace.

#### <a name="suggestion"></a>Návrh

Vývojář, který cílí na .NET Framework 4.7.2 nebo větší a chce se vrátit k chování algoritmu hash SHA1, musí nastavit následující příznak AppContext.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

Vývojář, který chce využít SHA256 hash při cílení na verzi architektury nižší než .NET 4.7.2, musí nastavit níže uvedený příznak AppContext.  Všimněte si, že nainstalovaná verze .NET Framework musí být 4.7.2 nebo vyšší.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Průhlednost |
| Verze | 4.7.2       |
| Typ    | Změna cílení |
