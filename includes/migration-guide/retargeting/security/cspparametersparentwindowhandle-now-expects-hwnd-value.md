---
ms.openlocfilehash: 72f907c117748fb19ca0663f24445a8c978afd32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235567"
---
### <a name="cspparametersparentwindowhandle-now-expects-hwnd-value"></a>CspParameters.ParentWindowHandle nyní očekává hodnotu HWND

|   |   |
|---|---|
|Podrobnosti|Hodnota <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> zavedená v rozhraní .NET Framework 2.0 umožňuje aplikaci zaregistrovat hodnotu popisovače nadřazeného okna tak, aby se libovolné rozhraní požadované pro přístup ke klíči (například výzva k zadání kódu PIN nebo dialogové okno souhlasu) otevřelo jako modální podřízený do zadaného okna. Počínaje aplikacemi, které cílí na rozhraní .NET Framework <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> 4.7, může aplikace Windows Forms nastavit vlastnost s následujícím kódem:<pre><code class="lang-csharp">cspParameters.ParentWindowHandle = form.Handle;&#13;&#10;</code></pre>V předchozích verzích rozhraní .NET Framework byla <xref:System.IntPtr?displayProperty=name> očekávaná hodnota představující umístění v paměti, kde byla umístěna hodnota [HWND.](https://docs.microsoft.com/windows/desktop/WinProg/windows-data-types#HWND) Nastavení vlastnosti do formuláře. Popisovač na Windows 7 a starší verze neměl žádný vliv, ale na &quot; <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>Windows 8 a novější verze, výsledkem je : Parametr je nesprávný.&quot;|
|Návrh|Aplikace, které cílí na rozhraní .NET Framework 4.7 nebo vyšší, které chtějí zaregistrovat vztah nadřazeného okna, se vyzývají k použití zjednodušeného formuláře:<pre><code class="lang-csharp">cspParameters.ParentWindowHandle = form.Handle;&#13;&#10;</code></pre>Uživatelé, kteří zjistili, že správná hodnota předat byla <code>form.Handle</code> adresa umístění v paměti, která držela <code>Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle</code> <code>true</code>hodnotu můžete odhlásit změny chování nastavením AppContext přepínač na :<ol><li>Programovým nastavením přepínačů compat na AppContext, jak je vysvětleno [zde](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</li><li>Přidáním následujícího řádku <code>&lt;runtime&gt;</code> do části souboru app.config:</li></ol><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Naopak uživatelé, kteří se chtějí přihlásit k novému chování v době běhu rozhraní .NET Framework 4.7, <code>false</code>když se aplikace načte pod staršími verzemi rozhraní .NET Framework, mohou nastavit přepínač AppContext na .|
|Rozsah|Vedlejší|
|Version|4.7|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Security.Cryptography.CspParameters.ParentWindowHandle?displayProperty=nameWithType></li></ul>|
