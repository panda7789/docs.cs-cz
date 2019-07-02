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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e846f45b55ac09d6ce6af4f3223c3bdba1dc83ba
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506011"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>Prostředky aplikací pro knihovny cílené na více platforem
Můžete použít rozhraní .NET Framework [přenosné knihovny tříd](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) projektu typu zajistit, že prostředky v knihovnách tříd můžete přistupovat z více platforem. Tento typ projektu je k dispozici v sadě Visual Studio 2012 a cílí na přenosné podmnožiny knihovny tříd rozhraní .NET Framework. Použití přenosné knihovny tříd zajišťuje, že vaše knihovna přístupná z aplikací klasické pracovní plochy, aplikace Silverlight, Windows Phone apps, a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 Umožňuje pouze velmi omezené dílčí sady typů v projektu knihovny přenosných tříd <xref:System.Resources> oboru názvů k dispozici pro aplikace, ale bylo možné použít <xref:System.Resources.ResourceManager> třídy pro načtení prostředků. Nicméně pokud vytváříte aplikace pomocí sady Visual Studio, měli byste použít obálky se silným typem vytvořené pomocí sady Visual Studio namísto použití <xref:System.Resources.ResourceManager> třídy přímo.

 Chcete-li v sadě Visual Studio vytvořit obálky se silným typem, nastavte hlavního souboru prostředku **modifikátor přístupu** v Návrháři prostředků do sady Visual Studio **veřejné**. Tím dojde k vytvoření souboru [resourceFileName].designer.cs nebo [resourceFileName].designer.vb, který obsahuje obálky ResourceManager se silným typem. Další informace o používání obálek prostředků se silnými typy, naleznete v tématu v části "Generování silně typované třídy prostředků" [Resgen.exe (Generátor zdrojových souborů)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) tématu.

## <a name="resource-manager-in-the-portable-class-library"></a>Správce prostředků v přenosné knihovny tříd
 V projektu knihovny přenosných tříd, veškerý přístup k prostředkům zpracováván pomocí <xref:System.Resources.ResourceManager> třídy. Protože typy, které do <xref:System.Resources> obor názvů, jako například <xref:System.Resources.ResourceReader> a <xref:System.Resources.ResourceSet>, není přístupný z projektu knihovny přenosných tříd, nelze je použít pro přístup k prostředkům.

 Knihovny přenosných tříd projektu zahrnuje čtyři <xref:System.Resources.ResourceManager> členy uvedené v následující tabulce. Tyto konstruktory a metody umožňují vytvořit instanci <xref:System.Resources.ResourceManager> objektu a načíst prostředky řetězců.

|`ResourceManager` Člen|Popis|
|------------------------------|-----------------|
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|Vytvoří <xref:System.Resources.ResourceManager> instance pro přístup k souboru s názvem prostředků nalezenému v zadaném sestavení.|
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|Vytvoří <xref:System.Resources.ResourceManager> instanci, která odpovídá zadaného typu.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|Načte pojmenovaný prostředek pro aktuální jazykovou verzi.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|Načte pojmenovaný prostředek, který patří do zadané jazykové verze.|

 Vyloučení jiných <xref:System.Resources.ResourceManager> členy z přenosné knihovny tříd znamená, že serializovat objekty, neřetězcová data a obrázky nelze načíst ze souboru prostředků. Chcete-li použít prostředky z přenosné knihovny tříd, byste měli uložit všechna data objektu ve formátu řetězce. Například můžete ukládat číselné hodnoty do souboru prostředků převedením na řetězce a načítat a převádět je na čísla pomocí číselného datového typu `Parse` nebo `TryParse` metody. Bitové kopie nebo jiná binární data můžete převést na řetězcové vyjádření pomocí volání <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> metoda a obnovení je bajt pole voláním <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType> metody.

## <a name="the-portable-class-library-and-windows-store-apps"></a>Přenosné knihovny tříd a aplikace Windows Store
 Přenosné knihovny tříd projektů uchovávat prostředky v souborech .resx, které jsou potom kompilovány do souborů .resources a vložit do hlavního sestavení nebo satelitního sestavení v době kompilace. [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, na druhé straně vyžadují prostředky k uložení souborů .resw, které jsou potom kompilovány do souboru prostředků (PRI) index jeden balíček. Bez ohledu na formátu souborů, ale přenosné knihovny tříd bude fungovat v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.

 Chcete-li využívat knihovnu tříd z [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikaci, přidejte na ni odkaz v projektu aplikace Windows Store. Visual Studio transparentně extrahuje prostředky z vašeho sestavení do souboru .resw a používá je ke generování souboru PRI, ze kterého modul Runtime Windows dokáže extrahovat prostředky. V době běhu modulu Windows Runtime spustí kód v přenosné knihovny tříd však získává vaše přenosné knihovny tříd prostředků ze souboru PRI.

 Pokud váš projekt knihovny přenosných tříd obsahuje lokalizované prostředky, je použít model střed a paprsek je nasadit stejně jako u knihovny aplikace klasické pracovní plochy. Chcete-li využívat hlavní soubor prostředků a všechny lokalizované soubory prostředků ve vaší [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikaci, přidejte odkaz na hlavní sestavení. V době kompilace sada Visual Studio extrahuje prostředky z hlavního souboru prostředků a všechny lokalizované soubory prostředků do samostatných souborů .resw. Poté kompiluje soubory .resw do jednoho souboru PRI, který přistupuje k prostředí Windows Runtime v době běhu.

<a name="NonLoc"></a>
## <a name="example-non-localized-portable-class-library"></a>Příklad: Nelokalizovaný přenosnou knihovnu tříd
 Následující příklad knihovny přenosných tříd jednoduché, nelokalizovaný používá prostředky k ukládání názvů sloupců a k určení počtu znaků, které mají vyhradit pro data tabulky. Příklad používá soubor s názvem LibResources.resx k uložení prostředků řetězců, které jsou uvedeny v následující tabulce.

|Název prostředku|Hodnota prostředku|
|-------------------|--------------------|
|Narozen/a|Datum narození|
|BornLength|12|
|Nástup|Datum nástupu|
|HiredLength|12|
|id|id|
|ID.Length|12|
|Name|Name|
|NameLength|25|
|Název|Databáze zaměstnanců|

 Následující kód definuje `UILibrary` třídu, která používá obálku správce prostředků s názvem `resources` vygenerované sadou Visual Studio při **modifikátor přístupu** pro souboru se změní na **veřejné** . Třída UILibrary analyzuje data řetězce podle potřeby. . Všimněte si, že třída je v `MyCompany.Employees` oboru názvů.

 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]

 Následující kód ukazuje, jak `UILibrary` třídy a jejím prostředkům můžete přistupovat z aplikace v režimu konzoly. Vyžaduje přidání odkazu na soubor UILibrary.dll do projektu aplikace konzoly.

 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]

 Následující kód ukazuje, jak `UILibrary` třídy a jejím prostředkům můžete přistupovat z [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace. Vyžaduje přidání odkazu na soubor UILibrary.dll do projektu aplikace Windows Store.

 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]

## <a name="example-localized-portable-class-library"></a>Příklad: Lokalizované přenosnou knihovnu tříd
 Následující lokalizovaný příklad knihovny přenosných tříd obsahuje prostředky pro francouzština (Francie) a jazykové verze Angličtina (Spojené státy). Jazyková verze Angličtina (Spojené státy) je výchozí jazykovou verzi aplikace; její prostředky jsou uvedeny v tabulce [předchozí části](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc). Soubor prostředků pro jazykovou verzi Francouzština (Francie) má název LibResources.fr-FR.resx a obsahuje prostředky řetězců, které jsou uvedeny v následující tabulce. Zdrojový kód `UILibrary` třída je stejný jako uvedeny v předchozí části.

|Název prostředku|Hodnota prostředku|
|-------------------|--------------------|
|Narozen/a|Date de naissance|
|BornLength|20|
|Nástup|Date embauché|
|HiredLength|16|
|id|id|
|Name|Nom|
|Název|Base de données des employés|

 Následující kód ukazuje, jak `UILibrary` třídy a jejím prostředkům můžete přistupovat z aplikace v režimu konzoly. Vyžaduje přidání odkazu na soubor UILibrary.dll do projektu aplikace konzoly.

 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]

 Následující kód ukazuje, jak `UILibrary` třídy a jejím prostředkům můžete přistupovat z [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace. Vyžaduje přidání odkazu na soubor UILibrary.dll do projektu aplikace Windows Store. Používá statickou `ApplicationLanguages.PrimaryLanguageOverride` vlastnosti chcete nastavit aplikaci upřednostňovaného jazyka na francouzštinu.

 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Resources.ResourceManager>
- [Prostředky v desktopových aplikacích](../../../docs/framework/resources/index.md)
- [Zabalení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
