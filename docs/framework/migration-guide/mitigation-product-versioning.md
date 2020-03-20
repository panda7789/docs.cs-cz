---
title: 'Zmírňující opatření: Správa verzí produktu'
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 64a68d2b79a0a3ccdd806949ffd6cb3760974390
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457820"
---
# <a name="mitigation-product-versioning"></a>Zmírňující opatření: Správa verzí produktu

V rozhraní .NET Framework 4.6 a novější chod verze produktu se změnil z předchozích verzí rozhraní .NET Framework (rozhraní .NET Framework 4, 4.5, 4.5.1 a 4.5.2).

## <a name="product-versioning-changes"></a>Změny správy verzí produktů

Níže jsou uvedeny podrobné změny:

- Hodnota položky `Version` v `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klíči se `4.6.`změnila na *xxxxx* pro rozhraní .NET Framework 4.6 a jeho bodové verze a `4.7.` *xxxxx* pro rozhraní .NET Framework 4.7. V rozhraní .NET Framework 4.5, 4.5.1 a 4.5.2 měl formát `4.5.` *xxxxx*.

- Správa verzí souborů a produktů pro soubory rozhraní .NET Framework `4.0.30319.x` `4.6.X.0` se změnila z dřívějšího schématu správy verzí `4.7.X.0` rozhraní .NET Framework 4.6 a jejích bodových verzí a na rozhraní .NET Framework 4.7 a jeho bodové verze. Tyto nové hodnoty můžete zobrazit při zobrazení **vlastností** souboru po kliknutí pravým tlačítkem myši na soubor.

- <xref:System.Reflection.AssemblyFileVersionAttribute> Atributy <xref:System.Reflection.AssemblyInformationalVersionAttribute> a pro spravovaná sestavení mají <xref:System.Version> hodnoty ve formuláři `4.6.X.0` pro rozhraní .NET Framework 4.6 a jeho bodové verze a `4.7.X.0` pro rozhraní .NET Framework 4.7.

- Počínaje rozhraním .NET Framework <xref:System.Environment.Version%2A?displayProperty=nameWithType> 4.6 vrátí `4.0.30319.42000`vlastnost řetězec pevné verze . V rozhraní .NET Framework 4, 4.5, 4.5.1 a 4.5.2 vrátí `4.0.30319.xxxxx` `xxxxx` řetězce verze ve formátu, kde je menší než 42000 (například "4.0.30319.18010"). Všimněte si, že nedoporučujeme kód aplikace <xref:System.Environment.Version%2A?displayProperty=nameWithType> s žádnou novou závislost na vlastnosti.

### <a name="handling-the-product-versioning-changes"></a>Zpracování změn správy verzí produktu

Obecně platí, že aplikace by měly záviset na doporučených technikách pro detekci takových věcí, jako je runtime verze rozhraní .NET Framework a instalačního adresáře:

- Chcete-li zjistit verzi rozhraní .NET Framework za běhu, [přečtěte si postup: Určení, které verze rozhraní .NET Framework jsou nainstalovány](how-to-determine-which-versions-are-installed.md).

- Chcete-li určit instalační cestu pro rozhraní .NET `InstallPath` Framework, `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` použijte hodnotu položky v klíči.

  > [!IMPORTANT]
  > Název podklíče `NET Framework Setup`je `.NET Framework Setup`, nikoli .

- Chcete-li určit cestu k adresáři ke spuštění <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> běžného jazyka rozhraní .NET Framework, zavolejte metodu.

- Chcete-li získat clr <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> verzi, volání metody.   Pro rozhraní .NET Framework 4 a jeho bodové verze (rozhraní .NET Framework 4.5, 4.5.1, 4.5.2 a .NET Framework 4.6, 4.6.1, 4.6.2 a 4.7) vrátí řetězec `v4.0.30319`.

## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
