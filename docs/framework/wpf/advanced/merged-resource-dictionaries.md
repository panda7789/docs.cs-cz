---
title: "Slovníky sloučených prostředků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- merged resource dictionaries [WPF]
- dictionaries [WPF], merged resources
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7ce02b772bacf2115a1bb74039fdff30a46fea8b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="merged-resource-dictionaries"></a>Slovníky sloučených prostředků
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]prostředky podporují funkci slovník sloučené prostředků. Tato funkce poskytuje způsob, jak definovat část prostředky [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace mimo zkompilovaný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplikace. Prostředky lze potom sdílen napříč aplikacemi a jsou také další pohodlně izolované pro lokalizaci.  
  
## <a name="introducing-a-merged-resource-dictionary"></a>Představení slovník sloučené prostředků  
 V kódu použijte následující syntaxi zavést slovník sloučené prostředků do stránky:  
  
 [!code-xaml[ResourceMergeDictionary#MergedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 Všimněte si, že <xref:System.Windows.ResourceDictionary> element nemá [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md), které se obecně požaduje pro všechny položky v kolekci prostředků. Ale jiné <xref:System.Windows.ResourceDictionary> odkazovat v rámci <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> kolekce je ve speciálním případě vyhrazena pro tento scénář slovník sloučené prostředků. <xref:System.Windows.ResourceDictionary> , Představuje sloučené nemůže mít slovník prostředků [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md). Obvykle každý <xref:System.Windows.ResourceDictionary> v rámci <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> určuje kolekci <xref:System.Windows.ResourceDictionary.Source%2A> atribut. Hodnota <xref:System.Windows.ResourceDictionary.Source%2A> by měla být [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] který přeloží na umístění souboru prostředků, který se má sloučit. Cílovým serverem, [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] musí být jiné [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru s <xref:System.Windows.ResourceDictionary> jako jeho kořenový element.  
  
> [!NOTE]
>  Je možné definovat prostředků v rámci <xref:System.Windows.ResourceDictionary> , který je určen jako slovník sloučené buď jako alternativu k určení <xref:System.Windows.ResourceDictionary.Source%2A>, nebo kromě ať prostředky jsou zahrnuty ze zadaného zdroje. Je to ale není běžný scénář; hlavní scénáře pro sloučené slovník je sloučit prostředky z externího souboru umístění. Pokud chcete určit prostředky v rámci značek pro stránku, měli byste obvykle definovat tyto v hlavní <xref:System.Windows.ResourceDictionary> a není v sloučené slovník.  
  
## <a name="merged-dictionary-behavior"></a>Chování sloučené slovník  
 Prostředky ve sloučené slovníku zabírají umístění v oboru vyhledávání prostředků, který je právě po oboru, které jsou sloučeny do slovníku hlavní prostředků. I když klíč prostředku musí být jedinečný v rámci všech jednotlivých slovník, klíč může existovat více než jednou. v sadě sloučené slovník. V takovém případě bude prostředek, který je vrácen pocházet ze slovníku poslední postupně ve <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> kolekce. Pokud <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> kolekce byla definovaná v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], pak pořadí sloučené slovníků v kolekci je pořadí prvků, jak je uvedeno ve značkách. Pokud klíč je definované ve slovníku primární a také v slovník, který byl sloučit, bude prostředek, který je vrácen pocházet ze slovníku primární. Toto rozsahu pravidla platí stejně pro statické prostředků odkazy a dynamické prostředků odkazy.  
  
### <a name="merged-dictionaries-and-code"></a>Sloučené slovník a kódu  
 Sloučené slovník mohou být přidány do `Resources` slovníku prostřednictvím kódu. Výchozí, původně prázdné <xref:System.Windows.ResourceDictionary> , existuje pro žádné `Resources` vlastnost má také výchozí původně prázdné <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> vlastnost kolekce. Přidání sloučené slovníku prostřednictvím kódu, získat odkaz na požadovanou primární <xref:System.Windows.ResourceDictionary>, získat jeho <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> hodnotu vlastnosti a volání `Add` na Obecné `Collection` obsažená v <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>. Musí být objekt přidáte nový <xref:System.Windows.ResourceDictionary>. V kódu není nastaveno <xref:System.Windows.ResourceDictionary.Source%2A> vlastnost. Místo toho je nutné získat <xref:System.Windows.ResourceDictionary> vytvořit nebo načítání jeden objekt. Dá se načíst existující <xref:System.Windows.ResourceDictionary> volat <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> na existujícím [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] datový proud souboru, který má <xref:System.Windows.ResourceDictionary> kořenové, pak přetypování <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> vrátit hodnotu <xref:System.Windows.ResourceDictionary>.  
  
### <a name="merged-resource-dictionary-uris"></a>Identifikátory URI slovník sloučené prostředků  
 Existuje několik postupů pro postup zahrnutí slovník sloučené prostředků, které jsou označeny [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] formátu, který budete používat. Obecně platí, že těchto postupů je možné rozdělit do dvou kategorií: prostředky, které zjišťují jako součást projektu a prostředky, které nejsou kompilovány jako součást projektu.  
  
 Pro prostředky, které zjišťují jako součást projektu můžete použít relativní cestu, která odkazuje na umístění prostředků. Relativní cesta se vyhodnotí během kompilace. Prostředek musí být definován jako součást projektu jako akce sestavení prostředků. Pokud zahrnete souboru XAML prostředků v projektu jako prostředek, není potřeba kopírovat soubor prostředků do výstupního adresáře, prostředek je už součástí sady v rámci kompilované aplikace. Můžete taky obsahu sestavení akce, ale musíte pak zkopírujte soubory do výstupního adresáře a také nasadit soubory prostředků v relaci stejný cesta ke spustitelnému souboru.  
  
> [!NOTE]
>  Nepoužívejte akce sestavení vložený prostředek. Vlastní akci sestavení je podporována pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, ale řešení <xref:System.Windows.ResourceDictionary.Source%2A> nebere v úvahu <xref:System.Resources.ResourceManager>a proto nelze oddělte jednotlivé prostředků z datového proudu. Vložený prostředek může dál používat pro jiné účely tak dlouho, dokud se také používá <xref:System.Resources.ResourceManager> pro přístup k prostředkům.  
  
 Související technik je použít Pack identifikátorů URI [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souborů a na ni odkazuje jako zdroj. Sada URI poskytuje odkazy na součástí odkazovaná sestavení a další metody. Další informace o identifikátorech URI Pack najdete v tématu [prostředek aplikace WPF, obsah a datové soubory](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).  
  
 Pro prostředky, které nejsou v rámci projektu kompilovány je identifikátor URI vyhodnocovány v době běhu. Běžné URI přenosu můžete použít jako soubor: nebo http: k naleznete v souboru prostředků. Nevýhodou použití přístupu noncompiled prostředků je tento soubor: přístup vyžaduje další kroky nasazení a http: přístupu znamená zóny zabezpečení Internetu.  
  
### <a name="reusing-merged-dictionaries"></a>Opětovné použití sloučené slovník  
 Můžete znovu použít nebo sdílet slovnících sloučené prostředků mezi aplikacemi, protože slovník prostředků sloučit lze odkazovat pomocí žádný platný [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]. Přesně tento postup bude záviset na strategie nasazení aplikací a jaké aplikace model, můžete postupovat podle. Zmíněnými strategie Pack URI poskytuje způsob, jak často zdroje sloučené prostředků ve více projektech během vývoje sdílením odkaz na sestavení. V tomto scénáři jsou prostředky stále distribuovat klienta a alespoň jedna z aplikací musíte nasadit odkazované sestavení. Také je možné odkazovat sloučené prostředkům prostřednictvím distribuované identifikátor URI, který používá protokol http.  
  
 Zápis sloučené slovník jako místní aplikace souborů nebo do místní sdílené úložiště je jiný možné sloučené slovník / scénář nasazení aplikace.  
  
### <a name="localization"></a>Lokalizace  
 Pokud prostředky, které je třeba lokalizovat izolují slovníky, které jsou sloučeny do primární slovník a zachovány jako uvolněná [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], tyto soubory je možné lokalizovat samostatně. Tento postup je lightweight alternativou k lokalizace satelitní sestavení prostředků. Podrobnosti najdete v tématu [WPF globalizace a lokalizace přehled](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.ResourceDictionary>  
 [Prostředky XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Prostředky a kódu](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [Prostředek aplikace WPF, obsahu a datových souborů](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
