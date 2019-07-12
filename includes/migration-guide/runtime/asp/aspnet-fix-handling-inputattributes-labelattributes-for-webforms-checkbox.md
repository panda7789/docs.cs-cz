---
ms.openlocfilehash: e605e0f2636d83745815ec4ed27bf72692f18d15
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802568"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a>Oprava zpracování technologie ASP.NET InputAttributes a LabelAttributes pro ovládací prvek zaškrtávací políčko webových formulářů

|   |   |
|---|---|
|Podrobnosti|U aplikací určených pro rozhraní .NET Framework 4.7.2 a předchozími verzemi <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> a <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> prostřednictvím kódu programu jsou přidané do webových formulářů <xref:System.Web.UI.WebControls.CheckBox> ovládacího prvku dojde ke ztrátě po zpětném volání. U aplikací určených pro rozhraní .NET Framework 4.8 nebo novější verze jsou zachovány po zpětném volání.|
|Doporučení|Pro správné chování pro obnovení atributy na zpětné volání, nastavte <code>targetFrameworkVersion</code> 4.8 nebo vyšší. Příklad:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Nastavení nižší nebo vůbec, zachová původní nesprávné chování.|
|Scope|Neznámé|
|Version|4.8|
|type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|

