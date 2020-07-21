---
title: 'Zmírňující opatření: Správa verzí produktu'
description: V tomto článku se dozvíte, jak se v předchozích verzích změnila .NET Framework 4,6 a novější verze produktu.
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 442c06446e763758d3a150ee9ff884a616541c07
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475395"
---
# <a name="mitigation-product-versioning"></a>Zmírňující opatření: Správa verzí produktu

V .NET Framework 4,6 a novějších verzích se verze produktu změnila z předchozích verzí .NET Framework (.NET Framework 4, 4,5, 4.5.1 a 4.5.2).

## <a name="product-versioning-changes"></a>Změny verzí produktu

Níže jsou uvedené podrobné změny:

- Hodnota `Version` položky v `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klíči se změnila na `4.6.` *xxxxx* pro .NET Framework 4,6 a její verze a na `4.7.` *xxxxx* pro .NET Framework 4,7. V .NET Framework 4,5, 4.5.1 a 4.5.2 má formát `4.5.` *xxxxx*.

- Verze souboru a produktu pro .NET Framework soubory se změnila ze staršího schématu správy verzí `4.0.30319.x` na `4.6.X.0` pro .NET Framework 4,6 a jeho vydání a na `4.7.X.0` pro .NET Framework 4,7 a jeho vydání. Tyto nové hodnoty se zobrazí po kliknutí pravým tlačítkem myši na soubor po zobrazení **vlastností** souboru.

- <xref:System.Reflection.AssemblyFileVersionAttribute>Atributy a <xref:System.Reflection.AssemblyInformationalVersionAttribute> pro spravovaná sestavení mají <xref:System.Version> hodnoty ve formátu `4.6.X.0` pro .NET Framework 4,6 a jeho vydání a `4.7.X.0` pro .NET Framework 4,7.

- Počínaje .NET Framework 4,6 <xref:System.Environment.Version%2A?displayProperty=nameWithType> vrátí vlastnost řetězec pevné verze `4.0.30319.42000` . V .NET Framework 4, 4,5, 4.5.1 a 4.5.2 vrátí řetězce verze ve formátu `4.0.30319.xxxxx` , kde `xxxxx` je méně než 42000 (například "4.0.30319.18010"). Všimněte si, že nedoporučujeme, aby se kód aplikace připustil jakékoli nové závislosti na <xref:System.Environment.Version%2A?displayProperty=nameWithType> Vlastnosti.

### <a name="handling-the-product-versioning-changes"></a>Zpracování změn verzí produktu

Obecně platí, že by aplikace měly záviset na doporučených technikách zjišťování, jako je běhová verze .NET Framework a instalační adresář:

- Chcete-li zjistit verzi modulu runtime .NET Framework, přečtěte si téma [How to: Určete, které verze .NET Framework jsou nainstalovány](how-to-determine-which-versions-are-installed.md).

- Chcete-li určit instalační cestu pro .NET Framework, použijte hodnotu `InstallPath` položky v `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klíči.

  > [!IMPORTANT]
  > Název podklíče není `NET Framework Setup` `.NET Framework Setup` .

- Chcete-li určit cestu k adresáři .NET Framework modulu CLR (Common Language Runtime), zavolejte <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> metodu.

- Chcete-li získat verzi CLR, zavolejte <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> metodu.   Pro .NET Framework 4 a jeho vydání (.NET Framework 4,5, 4.5.1, 4.5.2 a .NET Framework 4,6, 4.6.1, 4.6.2 a 4,7) vrátí řetězec `v4.0.30319` .

## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
