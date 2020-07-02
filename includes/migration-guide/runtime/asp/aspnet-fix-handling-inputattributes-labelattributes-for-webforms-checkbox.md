---
ms.openlocfilehash: ae557ce57557d027dba35b7da213c08aee85f2c7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621977"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a>ASP.NET opravovat zpracování ovládacího prvku zaškrtávací políčko InputAttributes a LabelAttributes pro WebForms

#### <a name="details"></a>Podrobnosti

Pro aplikace, které cílí na .NET Framework 4.7.2 a starší verze <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> a <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> které jsou programově přidány do ovládacího prvku webformaci, <xref:System.Web.UI.WebControls.CheckBox> se po zpětném odeslání ztratí. Pro aplikace, které cílí na .NET Framework 4,8 nebo novější verze, se po zpětném odeslání uchovávají.

#### <a name="suggestion"></a>Návrh

Pro správné chování při obnovování atributů při zpětném volání nastavte na <code>targetFrameworkVersion</code> 4,8 nebo vyšší. Příklad:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Jeho nastavení je nižší nebo vůbec nezachovává staré nesprávné chování.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Není známo|
|Verze|4,8|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|
