---
title: 'Zmírňující opatření: Správa verzí produktu'
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 63075136b7de4aeaa4f94c092996ae1829b449a7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126158"
---
# <a name="mitigation-product-versioning"></a>Zmírňující opatření: Správa verzí produktu

V .NET Framework 4,6 a novějších verzích se verze produktu změnila z předchozích verzí .NET Framework (.NET Framework 4, 4,5, 4.5.1 a 4.5.2).

## <a name="product-versioning-changes"></a>Změny verzí produktu

Níže jsou uvedené podrobné změny:

- Hodnota položky `Version` v klíči `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` se změnila na `4.6.`*xxxxx* pro .NET Framework 4,6 a jeho vydání a na `4.7.`*xxxxx* pro .NET Framework 4,7. V .NET Framework 4,5, 4.5.1 a 4.5.2 má formát `4.5.`*xxxxx*.

- Verze souboru a produktu pro .NET Framework se změnila ze staršího schématu verze `4.0.30319.x` na `4.6.X.0` pro .NET Framework 4,6 a jeho vydání a na `4.7.X.0` .NET Framework 4,7 a jeho vydání. Tyto nové hodnoty se zobrazí po kliknutí pravým tlačítkem myši na soubor po zobrazení **vlastností** souboru.

- Atributy <xref:System.Reflection.AssemblyFileVersionAttribute> a <xref:System.Reflection.AssemblyInformationalVersionAttribute> pro spravovaná sestavení mají <xref:System.Version> hodnoty ve tvaru `4.6.X.0` pro .NET Framework 4,6 a jeho vydání a `4.7.X.0` .NET Framework 4,7.

- Počínaje .NET Framework 4,6 vlastnost <xref:System.Environment.Version%2A?displayProperty=nameWithType> vrací `4.0.30319.42000`řetězce pevné verze. V .NET Framework 4, 4,5, 4.5.1 a 4.5.2 vrátí řetězce verze ve formátu `4.0.30319.xxxxx`, kde `xxxxx` je menší než 42000 (například "4.0.30319.18010"). Všimněte si, že kód aplikace nedoporučujeme mít žádnou novou závislost na vlastnosti <xref:System.Environment.Version%2A?displayProperty=nameWithType>.

### <a name="handling-the-product-versioning-changes"></a>Zpracování změn verzí produktu

Obecně platí, že by aplikace měly záviset na doporučených technikách zjišťování, jako je běhová verze .NET Framework a instalační adresář:

- Chcete-li zjistit verzi modulu runtime .NET Framework, přečtěte si téma [How to: Určete, které verze .NET Framework jsou nainstalovány](how-to-determine-which-versions-are-installed.md).

- Chcete-li určit instalační cestu pro .NET Framework, použijte hodnotu položky `InstallPath` v klíči `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`.

  > [!IMPORTANT]
  > Název podklíče je `NET Framework Setup`, nikoli `.NET Framework Setup`.

- Chcete-li určit cestu k adresáři .NET Framework modulu CLR (Common Language Runtime), zavolejte metodu <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType>.

- Chcete-li získat verzi CLR, zavolejte metodu <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType>.   Pro .NET Framework 4 a jeho vydání (.NET Framework 4,5, 4.5.1, 4.5.2 a .NET Framework 4,6, 4.6.1, 4.6.2 a 4,7) vrátí řetězec `v4.0.30319`.

## <a name="see-also"></a>Viz také:

- [Změny v modulu runtime](runtime-changes-in-the-net-framework-4-6.md)
