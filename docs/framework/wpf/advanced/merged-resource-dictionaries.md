---
title: Slovníky sloučených prostředků
ms.date: 03/30/2017
helpviewer_keywords:
- merged resource dictionaries [WPF]
- dictionaries [WPF], merged resources
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
ms.openlocfilehash: ae6c8dc3669ed46165f3d78e78735187ebbc3776
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377015"
---
# <a name="merged-resource-dictionaries"></a>Slovníky sloučených prostředků
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] prostředků podporují funkci slovníku prostředků. Tato funkce poskytuje způsob, jak definovat části prostředky [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace mimo zkompilovaný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplikace. Prostředky pak můžete sdílet mezi aplikací a také více pohodlně izolaci pro lokalizaci.  
  
## <a name="introducing-a-merged-resource-dictionary"></a>Úvod do slovníku prostředků  
 Ve značce použijte následující syntaxi zavést slovník prostředků do stránky:  
  
 [!code-xaml[ResourceMergeDictionary#MergedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 Všimněte si, že <xref:System.Windows.ResourceDictionary> prvek nemá [x: Key – direktiva](../../xaml-services/x-key-directive.md), které se obecně požaduje pro všechny položky v kolekci prostředků. Ale jiné <xref:System.Windows.ResourceDictionary> odkazů v rámci <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> kolekce je zvláštní případ, vyhrazena pro tento scénář slovníku prostředků. <xref:System.Windows.ResourceDictionary> , Který představuje sloučený slovník prostředků nemůže mít [x: Key – direktiva](../../xaml-services/x-key-directive.md). Obvykle každý <xref:System.Windows.ResourceDictionary> v rámci <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> určuje kolekci <xref:System.Windows.ResourceDictionary.Source%2A> atribut. Hodnota <xref:System.Windows.ResourceDictionary.Source%2A> by měl být [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] , který překládá do umístění souboru prostředků ke sloučení. Určení, která [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] musí být jiný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru, s <xref:System.Windows.ResourceDictionary> jako jeho kořenový element.  
  
> [!NOTE]
>  Je možné k definování prostředků v rámci <xref:System.Windows.ResourceDictionary> , který je uveden jako sloučeného slovníku, buď jako alternativu k určení <xref:System.Windows.ResourceDictionary.Source%2A>, nebo kromě libovolné prostředky jsou zahrnuty ze zadaného zdroje. Ale to není běžný scénář, kdy; hlavní scénáře pro sloučenými slovníky je sloučit prostředky z umístění externích souborů. Pokud chcete určit prostředky v rámci značky pro stránku, měli byste obvykle definovat v hlavním <xref:System.Windows.ResourceDictionary> a ne v sloučenými slovníky.  
  
## <a name="merged-dictionary-behavior"></a>Sloučený slovník chování  
 Prostředky v sloučeného slovníku zabírat umístění v rámci vyhledávání prostředků, které je bezprostředně po oboru jsou sloučeny do slovníku hlavní prostředků. I když klíč prostředku musí být jedinečný v rámci všechny jednotlivé slovníku, klíči může existovat více než jednou v sadě sloučenými slovníky. V tomto případě na prostředek, který je vrácen budou přicházet z poslední slovníku postupně v nalezen <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> kolekce. Pokud <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> kolekce byla definována v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], pak pořadí sloučenými slovníky v kolekci je pořadí prvků, jak je uvedeno v kódu. Pokud klíč je definován ve slovníku primární a také ve slovníku, která se slučuje, prostředek, který je vrácen budou přicházet z primární slovníku. Tyto pravidla vytváření oborů platí stejně pro odkazy na statické prostředky a dynamický prostředek odkazy.  
  
### <a name="merged-dictionaries-and-code"></a>Sloučenými slovníky a kódu  
 Lze přidat sloučenými slovníky `Resources` slovníku prostřednictvím kódu. Výchozí původně prázdným <xref:System.Windows.ResourceDictionary> , která existuje pro všechny `Resources` vlastnost má také výchozí původně prázdným <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> vlastnost kolekce. Přidání sloučeného slovníku prostřednictvím kódu, získání odkazu na požadovanou primární <xref:System.Windows.ResourceDictionary>, získat její <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> hodnotu vlastnosti a volání `Add` na Obecné `Collection` , který je součástí <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>. Musí být objekt přidáte nový <xref:System.Windows.ResourceDictionary>. V kódu není nastavený <xref:System.Windows.ResourceDictionary.Source%2A> vlastnost. Místo toho je nutné získat <xref:System.Windows.ResourceDictionary> vytvoří tak jediný nebo načítání jeden objekt. Jeden ze způsobů, jak načíst existující <xref:System.Windows.ResourceDictionary> volat <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> na existujícím [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] datového proudu souboru, který má <xref:System.Windows.ResourceDictionary> kořenový adresář, pak přetypování <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> návratovou hodnotu pro <xref:System.Windows.ResourceDictionary>.  
  
### <a name="merged-resource-dictionary-uris"></a>Identifikátory URI slovník prostředků  
 Existuje několik postupů pro zahrnutí slovník prostředků, které jsou označeny [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] formátu, který budete používat. Obecně vzato těchto postupů je možné rozdělit do dvou kategorií: prostředky, které jsou kompilovány jako součást projektu a prostředky, které nejsou kompilovány jako součást projektu.  
  
 Pro prostředky, které jsou kompilovány jako součást projektu můžete použít relativní cestu, která odkazuje na umístění prostředků. Relativní cesta se vyhodnotí během kompilace. Váš prostředek musí být definován jako součást projektu jako akci sestavení prostředků. Pokud zahrnete soubor .xaml prostředků v projektu jako prostředek, není potřeba kopírovat soubor prostředků do výstupního adresáře, prostředek je již součástí kompilované aplikace. Můžete také použít akci sestavení obsahu, ale musíte pak zkopírujte soubory do výstupního adresáře a nasadit také soubory prostředků ve stejné relaci cestu ke spustitelnému souboru.  
  
> [!NOTE]
>  Nepoužívejte akci vložený prostředek sestavení. Vlastní akci sestavení je podporováno pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací, ale rozlišení <xref:System.Windows.ResourceDictionary.Source%2A> nebere <xref:System.Resources.ResourceManager>a proto nelze oddělit jednotlivé prostředky z datového proudu. Můžete stále použít integrovaný prostředek pro jiné účely tak dlouho, dokud jste také použili <xref:System.Resources.ResourceManager> přístup k prostředkům.  
  
 Související technikou je identifikátory Pack URI pro použití [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru a označujeme jako zdroj. Identifikátor URI balíku umožňuje odkazy na součásti odkazovaná sestavení a další techniky. Další informace o identifikátory Pack URI najdete v tématu [prostředek aplikace WPF, obsah a datové soubory](../app-development/wpf-application-resource-content-and-data-files.md).  
  
 Pro prostředky, které nejsou kompilovány jako součást projektu identifikátor URI je vyhodnocen v době běhu. Například soubor můžete použít běžné přepravy identifikátoru URI: nebo http: k odkazování na soubor prostředků. Nevýhodou použití přístupu noncompiled prostředků je tento soubor: přístup vyžaduje další kroky nasazení a http: přístupu znamená zóny zabezpečení Internetu.  
  
### <a name="reusing-merged-dictionaries"></a>Opětovné použití sloučenými slovníky  
 Můžete opakovaně používat nebo sdílet slovníky sloučených prostředků mezi aplikacemi, protože slovník prostředků ke sloučení může být odkazováno prostřednictvím libovolného platný [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]. Přesně jak to provedete, bude záviset na vaší strategie nasazení aplikace a aplikaci, pro kterou modelu můžete postupovat podle. Výše uvedené identifikátory Pack URI strategie poskytuje způsob, jak často zdroje sloučených prostředků ve více projektech během vývoje sdílením odkaz na sestavení. V tomto scénáři prostředky stále rozdělené podle klienta a alespoň jednu z aplikací musíte nasadit odkazované sestavení. Je také možné odkazovat na sloučené prostředky prostřednictvím distribuované identifikátoru URI, který používá protokol http.  
  
 Zápis sloučenými slovníky jako místní aplikace soubory nebo na místní sdílené úložiště je další možné sloučeného slovníku / scénář nasazení aplikace.  
  
### <a name="localization"></a>Lokalizace  
 Pokud jsou izolované slovníky, které jsou sloučena s primární slovníky a uchovávat jako volné prostředky, které potřebují k lokalizování [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], tyto soubory mohou být lokalizována samostatně. Tento postup je jednoduchý alternativou k lokalizování sestavení satelitních prostředků. Podrobnosti najdete v tématu [přehled WPF globalizace a lokalizace](wpf-globalization-and-localization-overview.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.ResourceDictionary>
- [Prostředky XAML](xaml-resources.md)
- [Prostředky a kód](resources-and-code.md)
- [Prostředek, obsah a datové soubory aplikace WPF](../app-development/wpf-application-resource-content-and-data-files.md)
