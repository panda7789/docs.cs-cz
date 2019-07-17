---
ms.openlocfilehash: 72f907c117748fb19ca0663f24445a8c978afd32
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68235567"
---
### <a name="cspparametersparentwindowhandle-now-expects-hwnd-value"></a>CspParameters.ParentWindowHandle nyní očekává hodnotu HWND

|   |   |
|---|---|
|Podrobnosti|<xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> Hodnotu zavedena v rozhraní .NET Framework 2.0, umožňuje aplikaci zaregistrovat hodnotu popisovač nadřazené okno tak, aby všem prvkům uživatelského rozhraní pro přístup k klíč (jako je například PIN výzvu nebo souhlas dialogového okna) otevře jako modální podřízené určené okno. Počínaje aplikací určených pro rozhraní .NET Framework 4.7, můžete nastavit aplikaci Windows Forms <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> vlastnost s kódem, jako je následující:<pre><code class="lang-csharp">cspParameters.ParentWindowHandle = form.Handle;&#13;&#10;</code></pre>V předchozích verzích rozhraní .NET Framework, byla očekávána hodnota bude <xref:System.IntPtr?displayProperty=name> představující umístění v paměti, kde [HWND](https://docs.microsoft.com/windows/desktop/WinProg/windows-data-types#HWND) hodnotu nacházejí. Nastavení vlastnosti formuláře. Zpracování ve Windows 7 a starší verze nemělo žádný vliv, ale ve Windows 8 a novějších verzích je výsledkem &quot; <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>: Parametr je nesprávný.&quot;|
|Doporučení|Aplikace cílí na .NET Framework 4.7 nebo vyšší se chtějí registrovat nadřazené okno relace se doporučuje použít zjednodušený formulář:<pre><code class="lang-csharp">cspParameters.ParentWindowHandle = form.Handle;&#13;&#10;</code></pre>Uživatelé, kteří měli zjistili, že se správnou hodnotu pro předání adresy umístění v paměti, která je uložená hodnota <code>form.Handle</code> můžete vyjádřit výslovný nesouhlas Změna chování tak, že nastavíte přepínač AppContext <code>Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle</code> k <code>true</code>:<ol><li>Prostřednictvím kódu programu nastavením compat přepne na AppContext, jak je vysvětleno [tady](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</li><li>Přidejte následující řádek, který <code>&lt;runtime&gt;</code> část souboru app.config:</li></ol><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Naopak, uživatelé, kteří chtějí výslovný souhlas se nové chování na modul runtime rozhraní .NET Framework 4.7 při zatížení aplikací v rámci starší verze rozhraní .NET Framework můžete nastavit AppContext přepnout na <code>false</code>.|
|Scope|Vedlejší|
|Version|4.7|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.CspParameters.ParentWindowHandle?displayProperty=nameWithType></li></ul>|
