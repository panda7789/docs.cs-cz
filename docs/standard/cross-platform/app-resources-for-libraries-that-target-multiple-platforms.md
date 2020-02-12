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
ms.openlocfilehash: 3bf475117a85c2fced260dcc9460d55cd7007277
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123659"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>Prostředky aplikací pro knihovny cílené na více platforem
Typ projektu .NET Framework [přenosné knihovny tříd](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) můžete použít k zajištění toho, aby k prostředkům v knihovnách tříd bylo možné přicházet z více platforem. Tento typ projektu je k dispozici v sadě Visual Studio 2012 a cílí na přenosnou podmnožinu knihovny tříd .NET Framework. Použití přenositelné knihovny tříd zajišťuje, aby k vaší knihovně bylo možné přistupovat z aplikací klasické pracovní plochy, aplikací Silverlight, aplikací Windows Phone a aplikací pro Store ve Windows 8. x.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 Přenositelné projekty knihovny tříd zpřístupňují pouze velmi omezené podmnožiny typů v oboru názvů <xref:System.Resources> k dispozici pro vaši aplikaci, ale umožňuje použít třídu <xref:System.Resources.ResourceManager> k načtení prostředků. Pokud však vytváříte aplikaci pomocí sady Visual Studio, měli byste použít obálku se silným typem vytvořenou v aplikaci Visual Studio místo přímého použití třídy <xref:System.Resources.ResourceManager>.

 Chcete-li vytvořit obálku se silným typem v sadě Visual Studio, nastavte **modifikátor přístupu** hlavního souboru prostředků v Návrháři prostředků sady Visual Studio na **veřejné**. Tím dojde k vytvoření souboru [resourceFileName].designer.cs nebo [resourceFileName].designer.vb, který obsahuje obálky ResourceManager se silným typem. Další informace o použití obálky prostředků se silnými typy najdete v části "generování třídy prostředků se silnými typy" v tématu [Resgen. exe (generátor souboru prostředků)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) .

## <a name="resource-manager-in-the-portable-class-library"></a>Správce prostředků v přenositelné knihovně tříd
 V projektu přenositelné knihovny tříd je veškerý přístup k prostředkům zpracováván třídou <xref:System.Resources.ResourceManager>. Vzhledem k tomu, že typy v oboru názvů <xref:System.Resources>, například <xref:System.Resources.ResourceReader> a <xref:System.Resources.ResourceSet>, nejsou přístupné z přenositelného projektu knihovny tříd, nelze je použít pro přístup k prostředkům.

 Přenosná knihovna tříd obsahuje čtyři <xref:System.Resources.ResourceManager> členů uvedených v následující tabulce. Tyto konstruktory a metody umožňují vytvořit instanci objektu <xref:System.Resources.ResourceManager> a načíst řetězcové prostředky.

|`ResourceManager` člen|Popis|
|------------------------------|-----------------|
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|Vytvoří instanci <xref:System.Resources.ResourceManager> pro přístup k pojmenovanému souboru prostředků nalezeného v zadaném sestavení.|
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|Vytvoří instanci <xref:System.Resources.ResourceManager>, která odpovídá zadanému typu.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|Načte pojmenovaný prostředek pro aktuální jazykovou verzi.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|Načte pojmenovaný prostředek, který patří do zadané jazykové verze.|

 Vyloučení ostatních <xref:System.Resources.ResourceManager>ch členů z přenositelné knihovny tříd znamená, že v souboru prostředků nelze načíst Serializované objekty, data neřetězcového typu a obrázky. Chcete-li použít prostředky z přenositelné knihovny tříd, měli byste uložit všechna data objektů ve formě řetězce. Můžete například uložit číselné hodnoty do souboru prostředků jejich převodem na řetězce a pak je načíst a pak je převést zpět na čísla pomocí `Parse` nebo `TryParse` číselného datového typu. Můžete převést obrázky nebo jiná binární data na řetězcové vyjádření voláním metody <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> a obnovit je do pole bajtů voláním metody <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType>.

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
|Název|Název|
|NameLength|25|
|Název|Databáze zaměstnanců|

 Následující kód definuje třídu `UILibrary`, která používá Správce prostředků obálku s názvem `resources` vygenerovanou aplikací Visual Studio, když je **modifikátor přístupu** pro soubor změněn na **veřejné**. Třída UILibrary analyzuje data řetězce podle potřeby. . Všimněte si, že třída je v oboru názvů `MyCompany.Employees`.

 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]

 Následující kód ilustruje, jak lze ke třídě `UILibrary` a k jejím prostředkům přicházet z aplikace v režimu konzoly. Pro přidání do projektu konzolové aplikace vyžaduje odkaz na UILibrary. dll.

 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]

 Následující kód ilustruje, jak lze ke třídě `UILibrary` a k jejím prostředkům přicházet z aplikace Windows 8. x Store. Pro přidání do projektu aplikace pro Windows Store vyžaduje odkaz na UILibrary. dll.

 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]

## <a name="example-localized-portable-class-library"></a>Příklad: lokalizovaná Přenosná knihovna tříd
 Následující lokalizovaný příklad přenositelné knihovny tříd obsahuje prostředky pro jazykové verze francouzština (Francie) a angličtina (USA). Jazyková verze Angličtina (USA) je výchozí jazykovou verzí aplikace; jeho prostředky jsou uvedeny v tabulce v [předchozí části](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc). Soubor prostředků pro jazykovou verzi Francouzština (Francie) má název LibResources.fr-FR.resx a obsahuje prostředky řetězců, které jsou uvedeny v následující tabulce. Zdrojový kód pro třídu `UILibrary` je stejný, jak je uvedeno v předchozí části.

|Název prostředku|Hodnota prostředku|
|-------------------|--------------------|
|Narozen/a|Date de naissance|
|BornLength|20|
|Nástup|Date embauché|
|HiredLength|16|
|ID|ID|
|Název|Nom|
|Název|Base de données des employés|

 Následující kód ilustruje, jak lze ke třídě `UILibrary` a k jejím prostředkům přicházet z aplikace v režimu konzoly. Pro přidání do projektu konzolové aplikace vyžaduje odkaz na UILibrary. dll.

 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]

 Následující kód ilustruje, jak lze ke třídě `UILibrary` a k jejím prostředkům přicházet z aplikace Windows 8. x Store. Pro přidání do projektu aplikace pro Windows Store vyžaduje odkaz na UILibrary. dll. K nastavení preferovaného jazyka aplikace na francouzštinu používá vlastnost Static `ApplicationLanguages.PrimaryLanguageOverride`.

 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Resources.ResourceManager>
- [Prostředky v aplikacích klasické pracovní plochy](../../../docs/framework/resources/index.md)
- [Zabalení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
