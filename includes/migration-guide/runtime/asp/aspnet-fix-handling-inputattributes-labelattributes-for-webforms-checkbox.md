---
ms.openlocfilehash: ea0e1583cd611a624cf2d2edf9defb2294eb89d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802568"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a>ASP.NET Oprava zpracování atributů InputAttributes a LabelAttributes pro ovládací prvek Zaškrtávací políčko WebForms

|   |   |
|---|---|
|Podrobnosti|U aplikací, které cílí na rozhraní .NET <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> Framework <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> 4.7.2 a starší <xref:System.Web.UI.WebControls.CheckBox> verze a které jsou programově přidány do ovládacího prvku WebForms, budou po postbacku ztraceny. Pro aplikace, které cílí na rozhraní .NET Framework 4.8 nebo novější verze, jsou zachovány po postback.|
|Návrh|Pro správné chování pro obnovení atributů na <code>targetFrameworkVersion</code> postback, nastavte na 4,8 nebo vyšší. Například:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Nastavení nižší nebo vůbec ne, zachová staré nesprávné chování.|
|Rozsah|Není známo|
|Version|4.8|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|
