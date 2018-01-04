---
title: "Prostředky aplikací pro knihovny cílené na více platforem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7006c07d32a9f0adbafce1c83c1b29842f634a9a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>Prostředky aplikací pro knihovny cílené na více platforem
Můžete použít rozhraní .NET Framework [Přenosná knihovna tříd](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) projektu typu zajistit, aby prostředky ve vašich knihovnách třída je přístupná z více platforem. Tento typ projektu není k dispozici v [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] a cílem do něj podmnožinu Přenosná knihovna tříd rozhraní .NET Framework. Použití [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] zajistí, že vaše knihovna je přístupná z aplikace klasické pracovní plochy, aplikace Silverlight, aplikace Windows Phone, a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.  
  
 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] Umožňuje jenom velmi omezená podmnožina typy v projektu <xref:System.Resources> obor názvů, které jsou k dispozici pro aplikace, ale umožňují používat <xref:System.Resources.ResourceManager> třída pro načítání prostředků. Ale pokud vytváříte aplikace pomocí sady Visual Studio, používejte silného typu obálku vytvořené sadě Visual Studio místo použití <xref:System.Resources.ResourceManager> přímo třídu.  
  
 Pokud chcete silného typu obálku v sadě Visual Studio, nastavte souboru hlavní prostředků **– modifikátor přístupu** v Návrháři prostředků do sady Visual Studio **veřejné**. Tím dojde k vytvoření souboru [resourceFileName].designer.cs nebo [resourceFileName].designer.vb, který obsahuje obálky ResourceManager se silným typem. Další informace o používání obálku prostředků se silnými typy, najdete v části "Generování silně typované třídy prostředků" v [Resgen.exe (Generátor zdrojových souborů)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) tématu.  
  
## <a name="resource-manager-in-the-includenetportableincludesnet-portable-mdmd"></a>Resource Manager v[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]  
 V [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu, veškerý přístup k prostředkům se zpracovává souborem <xref:System.Resources.ResourceManager> třídy. Protože typy v <xref:System.Resources> obor názvů, například <xref:System.Resources.ResourceReader> a <xref:System.Resources.ResourceSet>, nejsou přístupné z [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu, jejich nelze použít pro přístup k prostředkům.  
  
 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] Projekt zahrnuje čtyři <xref:System.Resources.ResourceManager> členy uvedené v následující tabulce. Tyto konstruktorů a metod umožňují vytváření instancí <xref:System.Resources.ResourceManager> objektu a načtení řetězcové prostředky.  
  
|`ResourceManager`člen|Popis|  
|------------------------------|-----------------|  
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|Vytvoří <xref:System.Resources.ResourceManager> instance pro přístup k souboru s názvem prostředku v zadaném sestavení nalezen.|  
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|Vytvoří <xref:System.Resources.ResourceManager> instance, která odpovídá zadaného typu.|  
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|Načte pojmenovaný prostředek pro aktuální jazykovou verzi.|  
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|Načte pojmenovaný prostředek, který patří do zadané jazykové verze.|  
  
 Vyloučení jiné <xref:System.Resources.ResourceManager> členy z [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] znamená, že serializovat objekty, jiné než řetězec data a bitové kopie se nedají načíst ze souboru prostředků. K použití prostředků z [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], měli byste uložit všechna data objektu ve formátu řetězce. Například můžete ukládat číselné hodnoty v souboru prostředků jejich převedením na řetězce a můžete je znovu načíst a pak je převést na čísla pomocí číselný datový typ `Parse` nebo `TryParse` metoda. Bitové kopie nebo jiná binární data můžete převést na řetězcovou reprezentaci voláním <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> metoda a obnovení, aby bajt pole voláním <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType> metoda.  
  
## <a name="the-includenetportableincludesnet-portable-mdmd-and-windows-store-apps"></a>[!INCLUDE[net_portable](../../../includes/net-portable-md.md)] a aplikace pro Windows Store  
 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]projekty ukládat prostředky do soubory RESX, které jsou pak zkompiluje do soubory .resources a vložených v hlavní sestavení nebo satelitní sestavení při kompilaci. [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]aplikace, na druhé straně vyžadovat prostředky k uložení do .resw soubory, které jsou pak zkompiluje do souboru indexu (PRI) jeden balíček prostředků. Ale i přes nekompatibilní formátů vaše [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] bude fungovat v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.  
  
 Knihovny tříd z využívat [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, přidejte odkaz na jeho v projektu aplikace Windows Store. Visual Studio se transparentně extrahovat prostředky z vaší sestavení do souboru .resw a použít ho k generovat PRI soubor, ze kterého [!INCLUDE[wrt](../../../includes/wrt-md.md)] můžete rozbalit prostředky. V době běhu [!INCLUDE[wrt](../../../includes/wrt-md.md)] spustí kód na vaši [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], ale získává vaší Přenosná knihovna tříd prostředky ze souboru PRI.  
  
 Pokud vaše [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projekt obsahuje lokalizované prostředky, použít model střed a paprsek je nasadit stejně jako u knihovny v aplikace na ploše. Využívat hlavní zdrojového souboru a všechny lokalizované soubory prostředků ve vaší [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, přidejte odkaz na hlavní sestavení. V době kompilace sada Visual Studio extrahuje prostředky z hlavního souboru prostředků a všechny lokalizované soubory prostředků do samostatných souborů .resw. Následně zkompiluje soubory .resw do jednoho PRI souboru, který [!INCLUDE[wrt](../../../includes/wrt-md.md)] přistupuje k za běhu.  
  
<a name="NonLoc"></a>   
## <a name="example-non-localized-includenetportableincludesnet-portable-mdmd"></a>Příklad: Nelokalizováno[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]  
 Následující jednoduchý, Nelokalizováno [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] příklad používá prostředky k uložení názvy sloupců a k určení počtu znaků můžete vyhradit pro tabulková data. Příklad používá soubor s názvem LibResources.resx k uložení prostředků řetězců, které jsou uvedeny v následující tabulce.  
  
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
  
 Následující kód definuje `UILibrary` třídu, která využívá obálku správce prostředků s názvem `resources` vytvořen sadou Visual Studio při **– modifikátor přístupu** pro souboru se změní na **veřejné** . Třída UILibrary analyzuje data řetězce podle potřeby. . Všimněte si, že třída je v `MyCompany.Employees` oboru názvů.  
  
 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]  
  
 Následující kód ukazuje, jak `UILibrary` třídy a jejích prostředcích je přístupná z režimu konzoly aplikace. Vyžaduje přidání odkazu na soubor UILIbrary.dll do projektu aplikace konzoly.  
  
 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]  
  
 Následující kód ukazuje, jak `UILibrary` třídy a jejích prostředcích lze přistupovat z [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace. Vyžaduje přidání odkazu na soubor UILIbrary.dll do projektu aplikace pro Windows Store.  
  
 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]  
  
## <a name="example-localized-includenetportableincludesnet-portable-mdmd"></a>Příklad: lokalizované[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]  
 Následující lokalizované [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] příkladu obsahuje zdroje informací pro francouzština (Francie) a jazykové verze Angličtina (Spojené státy). Jazykové verze Angličtina (Spojené státy) je výchozí jazykovou verzi aplikace; její prostředky jsou uvedené v tabulce v [předchozí části](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc). Soubor prostředků pro jazykovou verzi Francouzština (Francie) má název LibResources.fr-FR.resx a obsahuje prostředky řetězců, které jsou uvedeny v následující tabulce. Zdrojový kód `UILibrary` třída je stejná jako zobrazená v předchozí části.  
  
|Název prostředku|Hodnota prostředku|  
|-------------------|--------------------|  
|Narozen/a|Date de naissance|  
|BornLength|20|  
|Nástup|Date embauché|  
|HiredLength|16|  
|ID|ID|  
|Název|Nom|  
|Název|Base de données des employés|  
  
 Následující kód ukazuje, jak `UILibrary` třídy a jejích prostředcích je přístupná z režimu konzoly aplikace. Vyžaduje přidání odkazu na soubor UILIbrary.dll do projektu aplikace konzoly.  
  
 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]  
  
 Následující kód ukazuje, jak `UILibrary` třídy a jejích prostředcích lze přistupovat z [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace. Vyžaduje přidání odkazu na soubor UILIbrary.dll do projektu aplikace pro Windows Store. Používá statickou `ApplicationLanguages.PrimaryLanguageOverride` vlastnost nastavující aplikace preferovaný jazyk francouzština.  
  
 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Resources.ResourceManager>  
 [Prostředky v desktopových aplikacích](../../../docs/framework/resources/index.md)  
 [Zabalení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
