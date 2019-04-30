---
ms.openlocfilehash: ea0e1583cd611a624cf2d2edf9defb2294eb89d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665596"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a>Oprava zpracování technologie ASP.NET InputAttributes a LabelAttributes pro ovládací prvek zaškrtávací políčko webových formulářů

|   |   |
|---|---|
|Podrobnosti|U aplikací určených pro rozhraní .NET Framework 4.7.2 a předchozími verzemi <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> a <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> prostřednictvím kódu programu jsou přidané do webových formulářů <xref:System.Web.UI.WebControls.CheckBox> ovládacího prvku dojde ke ztrátě po zpětném volání. U aplikací určených pro rozhraní .NET Framework 4.8 nebo novější verze jsou zachovány po zpětném volání.|
|Doporučení|Pro správné chování pro obnovení atributy na zpětné volání, nastavte <code>targetFrameworkVersion</code> 4.8 nebo vyšší. Příklad:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Nastavení nižší nebo vůbec, zachová původní nesprávné chování.|
|Rozsah|Neznámé|
|Version|4.8|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|
