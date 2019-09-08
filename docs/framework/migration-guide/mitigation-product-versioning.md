---
title: Zmírnění Správa verzí produktu
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91db9d8c6fccf75bc9025a9487517e8c55d016cc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779206"
---
# <a name="mitigation-product-versioning"></a>Zmírnění Správa verzí produktu

V .NET Framework 4,6 a novějších verzích se verze produktu změnila z předchozích verzí .NET Framework (.NET Framework 4, 4,5, 4.5.1 a 4.5.2).

## <a name="product-versioning-changes"></a>Změny verzí produktu

Níže jsou uvedené podrobné změny:

- Hodnota `Version` položky `4.7.` `4.6.` v klíči se změnila na xxxxx pro .NET Framework 4,6 a její verze a na xxxxx pro .NET Framework 4,7. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` V .NET Framework 4,5, 4.5.1 a 4.5.2 má formát `4.5.` *xxxxx*.

- Verze souboru a produktu pro .NET Framework soubory se změnila ze staršího schématu `4.0.30319.x` správy verzí na `4.6.X.0` pro .NET Framework 4,6 a jeho vydání a na `4.7.X.0` pro .NET Framework 4,7 a jeho vydání. Tyto nové hodnoty se zobrazí po kliknutí pravým tlačítkem myši na soubor po zobrazení **vlastností** souboru.

- <xref:System.Version> `4.7.X.0` `4.6.X.0` Atributy a pro<xref:System.Reflection.AssemblyInformationalVersionAttribute> spravovaná sestavení mají hodnoty ve formátu pro .NET Framework 4,6 a jeho vydání a pro .NET Framework 4,7. <xref:System.Reflection.AssemblyFileVersionAttribute>

- Počínaje .NET Framework 4,6 <xref:System.Environment.Version%2A?displayProperty=nameWithType> vrátí vlastnost řetězec `4.0.30319.42000`pevné verze. V .NET Framework 4, 4,5, 4.5.1 a 4.5.2 vrátí řetězce verze ve formátu `4.0.30319.xxxxx` , kde `xxxxx` je méně než 42000 (například "4.0.30319.18010"). Všimněte si, že nedoporučujeme, aby se <xref:System.Environment.Version%2A?displayProperty=nameWithType> kód aplikace připustil jakékoli nové závislosti na vlastnosti.

### <a name="handling-the-product-versioning-changes"></a>Zpracování změn verzí produktu

Obecně platí, že by aplikace měly záviset na doporučených technikách zjišťování, jako je běhová verze .NET Framework a instalační adresář:

- Chcete-li zjistit verzi modulu runtime .NET Framework, přečtěte si téma [How to: Určete, které verze .NET Framework jsou](how-to-determine-which-versions-are-installed.md)nainstalovány.

- Chcete-li určit instalační cestu pro .NET Framework, použijte hodnotu `InstallPath` položky `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` v klíči.

  > [!IMPORTANT]
  > `NET Framework Setup` Název`.NET Framework Setup`podklíče není.

- Chcete-li určit cestu k adresáři .NET Framework modulu CLR (Common Language Runtime <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> ), zavolejte metodu.

- Chcete-li získat verzi CLR, zavolejte <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> metodu.   Pro .NET Framework 4 a jeho vydání (.NET Framework 4,5, 4.5.1, 4.5.2 a .NET Framework 4,6, 4.6.1, 4.6.2 a 4,7) vrátí řetězec `v4.0.30319`.

## <a name="see-also"></a>Viz také:

- [Změny v modulu runtime](runtime-changes-in-the-net-framework-4-6.md)
