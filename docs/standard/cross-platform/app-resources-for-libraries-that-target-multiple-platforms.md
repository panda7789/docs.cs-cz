---
title: Prostředky aplikací pro knihovny cílené na více platforem
ms.date: 07/18/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- multiple platforms, resources for
- resources [.NET Framework]
- .NET Framework, resources when targeting multiple platforms
- resources, for multiple platforms
- targeting multiple platforms, resources for
ms.assetid: 72c76f0b-7255-4576-9261-3587f949669c
ms.openlocfilehash: a2d02a8ebe5e2611db3bc284bb022470ff77f601
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290354"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>Prostředky aplikací pro knihovny cílené na více platforem
Typ projektu .NET Framework [přenosné knihovny tříd](cross-platform-development-with-the-portable-class-library.md) můžete použít k zajištění toho, aby k prostředkům v knihovnách tříd bylo možné přicházet z více platforem. Tento typ projektu je k dispozici v sadě Visual Studio 2012 a cílí na přenosnou podmnožinu knihovny tříd .NET Framework. Použití přenositelné knihovny tříd zajišťuje, aby k vaší knihovně bylo možné přistupovat z aplikací klasické pracovní plochy, aplikací Silverlight, aplikací Windows Phone a aplikací pro Store ve Windows 8. x.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 Přenositelné projekty knihovny tříd zpřístupňují pouze velmi omezené podmnožiny typů v <xref:System.Resources> oboru názvů, který je k dispozici pro vaši aplikaci, ale umožňuje použít <xref:System.Resources.ResourceManager> třídu k načtení prostředků. Pokud však vytváříte aplikaci pomocí sady Visual Studio, měli byste použít obálku se silným typem vytvořenou v aplikaci Visual Studio namísto přímé použití <xref:System.Resources.ResourceManager> třídy.

 Chcete-li vytvořit obálku se silným typem v sadě Visual Studio, nastavte **modifikátor přístupu** hlavního souboru prostředků v Návrháři prostředků sady Visual Studio na **veřejné**. Tím dojde k vytvoření souboru [resourceFileName].designer.cs nebo [resourceFileName].designer.vb, který obsahuje obálky ResourceManager se silným typem. Další informace o použití obálky prostředků se silnými typy najdete v části "generování třídy prostředků se silnými typy" v tématu [Resgen. exe (generátor souboru prostředků)](../../framework/tools/resgen-exe-resource-file-generator.md) .

## <a name="resource-manager-in-the-portable-class-library"></a>Správce prostředků v přenositelné knihovně tříd
 V projektu přenositelné knihovny tříd je veškerý přístup k prostředkům zpracováván <xref:System.Resources.ResourceManager> třídou. Vzhledem k tomu, že typy v <xref:System.Resources> oboru názvů, například <xref:System.Resources.ResourceReader> a <xref:System.Resources.ResourceSet> , nejsou přístupné z přenositelného projektu knihovny tříd, nelze je použít pro přístup k prostředkům.

 Projekt přenositelné knihovny tříd obsahuje čtyři <xref:System.Resources.ResourceManager> členy uvedené v následující tabulce. Tyto konstruktory a metody umožňují vytvářet instance <xref:System.Resources.ResourceManager> objektu a načítat řetězcové prostředky.

|`ResourceManager`člen|Popis|
|------------------------------|-----------------|
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|Vytvoří <xref:System.Resources.ResourceManager> instanci pro přístup k pojmenovanému souboru prostředků nalezeného v zadaném sestavení.|
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|Vytvoří <xref:System.Resources.ResourceManager> instanci, která odpovídá zadanému typu.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|Načte pojmenovaný prostředek pro aktuální jazykovou verzi.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|Načte pojmenovaný prostředek, který patří do zadané jazykové verze.|

 Vyloučení dalších <xref:System.Resources.ResourceManager> členů z přenositelné knihovny tříd znamená, že Serializované objekty, neřetězcová data a obrázky nelze načíst ze souboru prostředků. Chcete-li použít prostředky z přenositelné knihovny tříd, měli byste uložit všechna data objektů ve formě řetězce. Můžete například uložit číselné hodnoty do souboru prostředků jejich převodem na řetězce a pak je načíst a pak je převést zpět na čísla pomocí číselného datového typu `Parse` nebo `TryParse` metody. Můžete převést obrázky nebo jiná binární data na řetězcové vyjádření voláním <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> metody a obnovit je do pole bajtů voláním <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType> metody.

## <a name="the-portable-class-library-and-windows-store-apps"></a>Přenosná knihovna tříd a aplikace pro Windows Store
 Přenositelné knihovny tříd projekty ukládají prostředky v souborech. resx, které jsou poté zkompilovány do souborů. Resources a vloženy do hlavního sestavení nebo do satelitních sestavení v době kompilace. Aplikace Windows 8. x Store na druhé straně vyžadují uložení prostředků do souborů. resw, které se pak zkompiluje do jednoho souboru indexu prostředků balíčku (PRI). Nicméně navzdory nekompatibilním formátům souborů bude vaše Přenosná knihovna tříd fungovat v aplikaci Windows 8. x Store.

 Pokud chcete knihovnu tříd využít z aplikace Windows 8. x Store, přidejte na ni odkaz v projektu aplikace pro Windows Store. Visual Studio transparentně extrahuje prostředky ze sestavení do souboru. resw a použije ho k vygenerování souboru PRI, ze kterého může prostředí Windows Runtime extrahovat prostředky. V době běhu prostředí Windows Runtime spustí kód v přenositelné knihovně tříd, ale načte prostředky přenositelné knihovny tříd ze souboru PRI.

 Pokud Váš přenosný projekt knihovny tříd obsahuje lokalizované prostředky, použijte model hvězdicové lokality k jejich nasazení stejně jako knihovnu v desktopové aplikaci. Chcete-li využívat hlavní zdrojový soubor a všechny lokalizované soubory prostředků v aplikaci Windows 8. x Store, přidejte odkaz na hlavní sestavení. V době kompilace sada Visual Studio extrahuje prostředky z hlavního souboru prostředků a všechny lokalizované soubory prostředků do samostatných souborů .resw. Potom zkompiluje soubory. resw do jediného souboru PRI, ke kterému prostředí Windows Runtime přistupuje za běhu.

<a name="NonLoc"></a>
## <a name="example-non-localized-portable-class-library"></a>Příklad: nelokalizovaná Přenosná knihovna tříd
 Následující jednoduchá, nelokalizovaná knihovna tříd – příklad používá zdroje k ukládání názvů sloupců a určení počtu znaků, které se mají rezervovat pro tabulková data. Příklad používá soubor s názvem LibResources.resx k uložení prostředků řetězců, které jsou uvedeny v následující tabulce.

|Název prostředku|Hodnota prostředku|
|-------------------|--------------------|
|Narozen/a|Datum narození|
|BornLength|12|
|Nástup|Datum nástupu|
|HiredLength|12|
|ID|ID|
|ID.Length|12|
|Name|Name|
|NameLength|25|
|Nadpis|Databáze zaměstnanců|

 Následující kód definuje `UILibrary` třídu, která používá správce prostředků obálky s názvem `resources` vygenerovanou aplikací Visual Studio, když je **modifikátor přístupu** pro soubor změněn na **veřejné**. Třída UILibrary analyzuje data řetězce podle potřeby. . Všimněte si, že třída je v `MyCompany.Employees` oboru názvů.

 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]

 Následující kód ilustruje, jak `UILibrary` lze ke třídě a jejím prostředkům přicházet z aplikace v režimu konzoly. Pro přidání do projektu konzolové aplikace vyžaduje odkaz na UILibrary. dll.

 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]

 Následující kód ilustruje, jak `UILibrary` lze ke třídě a jejím prostředkům přicházet z aplikace Windows 8. x Store. Pro přidání do projektu aplikace pro Windows Store vyžaduje odkaz na UILibrary. dll.

 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]

## <a name="example-localized-portable-class-library"></a>Příklad: lokalizovaná Přenosná knihovna tříd
 Následující lokalizovaný příklad přenositelné knihovny tříd obsahuje prostředky pro jazykové verze francouzština (Francie) a angličtina (USA). Jazyková verze Angličtina (USA) je výchozí jazykovou verzí aplikace; jeho prostředky jsou uvedeny v tabulce v [předchozí části](app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc). Soubor prostředků pro jazykovou verzi Francouzština (Francie) má název LibResources.fr-FR.resx a obsahuje prostředky řetězců, které jsou uvedeny v následující tabulce. Zdrojový kód `UILibrary` třídy je stejný, jak je uvedeno v předchozí části.

|Název prostředku|Hodnota prostředku|
|-------------------|--------------------|
|Narozen/a|Date de naissance|
|BornLength|20|
|Nástup|Date embauché|
|HiredLength|16|
|ID|ID|
|Name|Nom|
|Nadpis|Base de données des employés|

 Následující kód ilustruje, jak `UILibrary` lze ke třídě a jejím prostředkům přicházet z aplikace v režimu konzoly. Pro přidání do projektu konzolové aplikace vyžaduje odkaz na UILibrary. dll.

 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]

 Následující kód ilustruje, jak `UILibrary` lze ke třídě a jejím prostředkům přicházet z aplikace Windows 8. x Store. Pro přidání do projektu aplikace pro Windows Store vyžaduje odkaz na UILibrary. dll. Používá statickou `ApplicationLanguages.PrimaryLanguageOverride` vlastnost k nastavení preferovaného jazyka aplikace na francouzštinu.

 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Resources.ResourceManager>
- [Prostředky v aplikacích klasické pracovní plochy](../../framework/resources/index.md)
- [Zabalení a nasazení prostředků](../../framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
