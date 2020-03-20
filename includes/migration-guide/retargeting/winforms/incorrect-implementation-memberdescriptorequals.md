---
ms.openlocfilehash: 01c0689bbfb102f8f4d9455f9d258e8ea5515d9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859350"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a>Nesprávná implementace memberDescriptor.Equals

|   |   |
|---|---|
|Podrobnosti|Původní implementace <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> metody porovnává dvě různé vlastnosti řetězce z porovnávaných objektů: název kategorie a řetězec popisu. <xref:System.ComponentModel.MemberDescriptor.Category> Oprava je porovnat první objekt s <xref:System.ComponentModel.MemberDescriptor.Category> druhým a <xref:System.ComponentModel.MemberDescriptor.Description> první ho <xref:System.ComponentModel.MemberDescriptor.Description> druhého.|
|Návrh|Pokud vaše aplikace <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> závisí <code>false</code> na někdy vrací, když popisovače jsou ekvivalentní a cílíte na rozhraní .NET Framework 4.6.2 nebo novější, máte několik možností:<ol><li>Proveďte změny kódu <xref:System.ComponentModel.MemberDescriptor.Category> <xref:System.ComponentModel.MemberDescriptor.Description> pro porovnání polí a <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> ručně kromě volání metody.</li><li>Odhlásit se z této změny přidáním následující hodnoty do souboru app.config:</li></ol><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Pokud vaše aplikace cílí na rozhraní .NET Framework 4.6.1 nebo starší a běží v rozhraní .NET Framework 4.6.2 nebo novější mj. <code>false</code><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.6.2|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType></li></ul>|
