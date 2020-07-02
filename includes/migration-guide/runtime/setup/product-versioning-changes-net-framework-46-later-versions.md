---
ms.openlocfilehash: a5c6dda0c1d68468cd95f67716709dd059948c80
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621148"
---
### <a name="product-versioning-changes-in-the-net-framework-46-and-later-versions"></a>Změny verzí produktu v .NET Framework 4,6 a novějších verzích

#### <a name="details"></a>Podrobnosti

Verze produktu se změnila z předchozích verzí .NET Framework, a to zejména z .NET Framework 4, 4,5, 4.5.1 a 4.5.2. Níže jsou uvedené podrobné změny:<ul><li>Hodnota <code>Version</code> položky v <code>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full</code> klíči se změnila na <code>4.6.xxxxx</code> pro .NET Framework 4,6 a její vydání a na <code>4.7.xxxxx</code> .NET Framework 4,7 a 4.7.1. V .NET Framework 4,5, 4.5.1 a 4.5.2 má formát <code>4.5.xxxxx</code> .</li><li>Verze souboru a produktu pro .NET Framework soubory se změnila ze staršího schématu správy verzí 4.0.30319. x na 4.6. X. 0 pro .NET Framework 4,6 a jeho vydání a na hodnotu 4.7. X. 0 pro .NET Framework 4,7 a 4.7.1. Tyto nové hodnoty se zobrazí po kliknutí pravým tlačítkem myši na soubor po zobrazení vlastností souboru.</li><li><xref:System.Reflection.AssemblyFileVersionAttribute>Atributy a <xref:System.Reflection.AssemblyInformationalVersionAttribute> pro spravovaná sestavení mají hodnoty verze ve formátu 4.6. X. 0 pro .NET Framework 4,6 a jejich vydání bodů a 4.7. X. 0 pro .NET Framework 4,7 a 4.7.1.</li><li>V .NET Framework 4,6, 4.6.1, 4.6.2, 4,7 a 4.7.1 <xref:System.Environment.Version?displayProperty=nameWithType> vrátí vlastnost řetězec pevné verze <code>4.0.30319.42000</code> . V .NET Framework 4, 4,5, 4.5.1 a 4.5.2 vrátí řetězce verze ve formátu <code>4.0.30319.xxxxx</code> (například &quot; 4.0.30319.18010 &quot; ). Všimněte si, že nedoporučujeme kód aplikace, který by měl mít žádnou novou závislost na vlastnosti prostředí. Version.</li></ul>Další informace najdete v tématu [Postup: určení, které verze .NET Framework jsou nainstalovány](~/docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).

#### <a name="suggestion"></a>Návrh

Obecně platí, že by aplikace měly záviset na doporučených technikách zjišťování, jako je běhová verze .NET Framework a instalační adresář:<ul><li>Chcete-li zjistit verzi modulu runtime .NET Framework, přečtěte si téma [How to: Určete, které verze .NET Framework jsou nainstalovány](~/docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</li><li>Chcete-li určit instalační cestu pro .NET Framework, použijte hodnotu <code>InstallPath</code> položky v <code>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full</code> klíči.</li></ul> <blockquote> [!IMPORTANT] Název podklíče není <code>NET Framework Setup</code> <code>.NET Framework Setup</code> .</blockquote> <ul><li>Chcete-li určit cestu k adresáři .NET Framework modulu CLR (Common Language Runtime), zavolejte <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory?displayProperty=nameWithType> metodu.</li><li>Chcete-li získat verzi CLR, zavolejte <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion?displayProperty=nameWithType> metodu. Pro .NET Framework 4 a jejich vydané verze (.NET Framework 4,5, 4.5.1, 4.5.2 a .NET Framework 4,6, 4.6.1, 4.6.2, 4,7 a 4.7.1) vrátí řetězec v 4.0.30319.</li></ul>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.6|
|Typ|Modul runtime|
