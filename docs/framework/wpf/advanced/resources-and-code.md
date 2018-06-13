---
title: Zdroje a kód
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys [WPF], using objects as
- resources [WPF], accessing from procedural code
- procedural code [WPF], creating resources with
- procedural code [WPF], accessing resources from
- resources [WPF], creating with procedural code
ms.assetid: c1cfcddb-e39c-41c8-a7f3-60984914dfae
ms.openlocfilehash: 27b72d4be9012caf388c90d52a61d9837713c71f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547544"
---
# <a name="resources-and-code"></a>Zdroje a kód
Tento přehled soustřeďuje na postupy [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] prostředky můžete přistupovat ani je vytvářet pomocí kódu místo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] syntaxe. Další informace o využití obecné prostředků a prostředky z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxe perspektivy, najdete v části [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
  
  
<a name="accessing"></a>   
## <a name="accessing-resources-from-code"></a>Přístup k prostředkům z kódu  
 Klíče, které označují prostředky, pokud jsou definovány na základě [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] se taky používají k načtení specifické prostředky, pokud požádáte o prostředku v kódu. Nejjednodušší způsob, jak načíst prostředek z kódu je volat buď <xref:System.Windows.FrameworkElement.FindResource%2A> nebo <xref:System.Windows.FrameworkElement.TryFindResource%2A> metoda z úrovni rozhraní objektů v aplikaci. Chování rozdíl mezi tyto metody je, co se stane, pokud není nalezen požadovaný klíč. <xref:System.Windows.FrameworkElement.FindResource%2A> vyvolá výjimku. <xref:System.Windows.FrameworkElement.TryFindResource%2A> nebude vyvolat výjimku, ale vrátí `null`. Každá metoda přebírá klíč prostředku jako vstupní parametr a vrátí objekt volného typu. Obvykle klíč prostředku je řetězec, ale existují příležitostně neřetězcový použití; najdete v článku [pomocí objektů jako klíče](#objectaskey) podrobnosti. Obvykle by přetypovat na typ vyžadují vlastnost, která nastavíte žádosti o prostředek vráceného objektu. Vyhledávání logiku pro překlad kódu prostředků je stejná jako odkaz na dynamické prostředků [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] případu. Hledat prostředky spustí z volání prvku a potom pokračuje v následných nadřazené elementy v logickém stromu. Vyhledávání bude pokračovat a vyšší do prostředky aplikace, motivů a systémové prostředky v případě potřeby. Žádost o kód pro prostředek bude správně účet pro změny v modulu runtime ve slovnících prostředků, které byly provedeny po této slovník prostředků, které jsou načítány z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]a také pro změny prostředků systému v reálném čase.  
  
 Tady je příklad stručný kódu, který vyhledá prostředku pomocí klíče a používá vrácené hodnoty pro nastavení vlastnosti, implementovaný jako <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužné rutiny události.  
  
 [!code-csharp[PropertiesOvwSupport#ResourceProceduralGet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#resourceproceduralget)]
 [!code-vb[PropertiesOvwSupport#ResourceProceduralGet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#resourceproceduralget)]  
  
 Je to alternativní metoda pro přiřazení odkaz prostředků <xref:System.Windows.FrameworkElement.SetResourceReference%2A>. Tato metoda přebírá dva parametry: klíč prostředek a identifikátor pro vlastnost konkrétní závislosti, který je přítomen v instanci element, ke kterému by se měla přiřadit hodnotu zdroje. Funkčně tato metoda je stejný a nabízí výhodu v podobě které nevyžadují žádné přetypování návratové hodnoty.  
  
 Ještě další způsob, jak přistupovat k prostředkům prostřednictvím kódu programu je pro přístup k obsahu <xref:System.Windows.FrameworkElement.Resources%2A> vlastnost jako slovník. Přístup slovníku obsažený v této vlastnosti je také jak přidáte nové prostředky do existující kolekce, zkontrolujte, když se už používá daný název klíče v kolekci a další operace slovník nebo kolekce. Pokud píšete [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikaci zcela v kódu, můžete také vytvořit celou kolekci v kódu, přiřadit klíčů a potom přiřadit dokončení kolekce k <xref:System.Windows.FrameworkElement.Resources%2A> vlastnost zavedených elementu. To bude popsané v další části.  
  
 Mohou indexu v rámci všechny zadané <xref:System.Windows.FrameworkElement.Resources%2A> shromažďování, použití konkrétního klíče jako index, ale měli vědět, že přístup k prostředku tímto způsobem nedodrží normální runtime pravidla prostředků řešení. Jsou pouze přístup k této konkrétní kolekce. Vyhledávání prostředků nebude možné procházení oboru kořenové nebo aplikace Pokud na požadovaný klíč byl nalezen žádný platný objekt. Tento přístup, ale může mít výhody výkonu v některých případech právě proto rozsah hledání klíče je omezené více. Najdete v článku <xref:System.Windows.ResourceDictionary> třída další podrobnosti o tom, jak pracovat s slovník prostředků přímo.  
  
<a name="creating"></a>   
## <a name="creating-resources-with-code"></a>Vytváření prostředků pomocí kódu  
 Pokud chcete vytvořit celou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace v kódu, můžete také chtít vytvořit všechny prostředky v této aplikaci v kódu. Jak toho docílit, vytvořte novou <xref:System.Windows.ResourceDictionary> instance a poté přidejte všechny prostředky do slovníku pomocí následná volání <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>. Potom použít <xref:System.Windows.ResourceDictionary> proto vytvořit nastavit <xref:System.Windows.FrameworkElement.Resources%2A> vlastnost u elementu, který se nachází v oboru stránky, nebo <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>. Můžete také zachovat <xref:System.Windows.ResourceDictionary> jako samostatném objektu bez přidání elementu. Ale pokud to uděláte, můžete musí přístup k prostředkům v něm pomocí klíče položky, jako by šlo obecné slovník. A <xref:System.Windows.ResourceDictionary> , není připojen k elementu `Resources` vlastnost, nebude existovat v rámci stromu elementu a nemá žádný obor v pořadí vyhledávání, které mohou být využívána <xref:System.Windows.FrameworkElement.FindResource%2A> a související metody.  
  
<a name="objectaskey"></a>   
## <a name="using-objects-as-keys"></a>Použití objektů jako klíče  
 Většina použití prostředků nastaví klíč na řetězec prostředku. Však různé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce úmyslně nepoužívají typu string nastavit klíče, místo toho tento parametr je objekt. Funkce s prostředku s klíči objekt je používán [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Podpora stylu a motivů. Každý styly v motivy, které se stanou výchozí styl pro ovládací prvek jinak bez stylem jsou klíčovány pomocí <xref:System.Type> ovládacího prvku, který by se měly používat k. Probíhá s klíči typu poskytuje spolehlivé vyhledávání mechanismus, který funguje na výchozí instance každé – typ ovládacího prvku a typ můžete zjištěno pomocí reflexe a používá pro určení stylu odvozené třídy, i když odvozený typ, jinak hodnota nemá žádné výchozí styl. Můžete zadat <xref:System.Type> klíče pro prostředek definované v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pomocí [x: Type – rozšíření značek](../../../../docs/framework/xaml-services/x-type-markup-extension.md). Podobně jako rozšíření pro další použití klíče neřetězcový, které podporují neexistují [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce, jako například [ComponentResourceKey – rozšíření značek](../../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md).  
  
## <a name="see-also"></a>Viz také  
 [Prostředky XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)
