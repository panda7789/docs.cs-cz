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
ms.openlocfilehash: 12f9acccfc23364795cd18ef1da2ced5b442c6f7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367974"
---
# <a name="resources-and-code"></a>Zdroje a kód
Tento přehled se soustřeďuje na tom [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] prostředkům můžou přistupovat ani je vytvářet pomocí kódu spíše než [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] syntaxe. Další informace o využití obecné prostředků a prostředků z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] perspektivy syntaxe, naleznete v tématu [prostředky XAML](xaml-resources.md).  
  
  
  
<a name="accessing"></a>   
## <a name="accessing-resources-from-code"></a>Přístup k prostředkům z kódu  
 Klíče, které označují prostředky, pokud jsou definovány prostřednictvím [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] také umožňují načíst konkrétní prostředky, pokud jste požádali o prostředku v kódu. Nejjednodušší způsob, jak získat zdroje z kódu je volání buď <xref:System.Windows.FrameworkElement.FindResource%2A> nebo <xref:System.Windows.FrameworkElement.TryFindResource%2A> metoda úrovni rozhraní objekty ve vaší aplikaci. Chování rozdíl mezi tyto metody je, co se stane, pokud požadovaný klíč nebyl nalezen. <xref:System.Windows.FrameworkElement.FindResource%2A> vyvolá výjimku. <xref:System.Windows.FrameworkElement.TryFindResource%2A> nevyvolá výjimku, ale vrátí `null`. Každá metoda používá klíč prostředku jako vstupní parametr a vrátí objekt volného typu. Obvykle klíč prostředku je řetězec, ale existují neřetězcový příležitostné použití; Zobrazit [použití objektů jako klíče](#objectaskey) podrobné informace. Obvykle by přetypovat vráceného objektu na typ vyžaduje vlastnost, která nastavujete při požadování prostředku. Logika vyhledávání pro rozlišení zdrojů kód je stejný jako odkaz na prostředek dynamické [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] případ. Hledat prostředky spustí z elementu volání a pak bude pokračovat po sobě jdoucích nadřazené prvky v logickém stromu. Vyhledávání bude pokračovat a vyšší do prostředků aplikace, motivy a systémové prostředky v případě potřeby. Žádost o kódu pro určitý prostředek se správně účet pro změny v modulu runtime ve slovnících prostředků, které provedly, může být od tohoto slovníku prostředků načítané z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]a také pro změn prostředků systému v reálném čase.  
  
 Tady je příklad stručný kódu, který vyhledá prostředek klíčem a používá vrácené hodnoty nastavení vlastnosti implementovaná jako <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužné rutiny události.  
  
 [!code-csharp[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#resourceproceduralget)]
 [!code-vb[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#resourceproceduralget)]  
  
 Je alternativní metoda pro přiřazení odkazu prostředku <xref:System.Windows.FrameworkElement.SetResourceReference%2A>. Tato metoda přebírá dva parametry: klíč prostředku a identifikátor pro vlastnost konkrétní závislosti, který je přítomen v instanci elementu, ke kterému by měly přiřazena hodnota prostředku. Tato metoda funkčně stejný a nabízí výhodu v podobě nevyžaduje žádné přetypování návratové hodnoty.  
  
 Je ještě další způsob, jak programově přistupovat k prostředkům pro přístup k obsahu <xref:System.Windows.FrameworkElement.Resources%2A> vlastnost jako slovník. Přístup k slovníku obsažen v této vlastnosti je také jak můžete přidat nové prostředky do existujících kolekcí, zkontrolujte, jestli daný název klíče se už používá v kolekci a další operace kolekce nebo slovníku. Při psaní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace kompletně v kódu, můžete také vytvořit celou kolekci v kódu, přiřadit klíče a potom přiřadit dokončení kolekci, která se <xref:System.Windows.FrameworkElement.Resources%2A> vlastnost zavedené prvku. To budou popsané v další části.  
  
 Můžete indexu v rámci každá <xref:System.Windows.FrameworkElement.Resources%2A> shromažďování, použití konkrétního klíče jako index, ale měli vědět, že přístup k prostředku tímto způsobem nedodržuje normální runtime pravidla prostředků řešení. Pouze při přístupu k této konkrétní kolekce. Vyhledání prostředku nebude být procházení obor na kořen nebo aplikace Pokud na požadovaný klíč nebyl nalezen žádný platný objekt. Tento přístup však může mít výhody výkonu v některých případech přesně, protože rozsah vyhledávání pro klíč je omezená více. Zobrazit <xref:System.Windows.ResourceDictionary> třídy podrobné informace o tom, jak pracovat s slovník prostředků přímo.  
  
<a name="creating"></a>   
## <a name="creating-resources-with-code"></a>Vytváření prostředků s kódem  
 Pokud chcete vytvořit celou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace v kódu, můžete také chtít vytvořit všechny prostředky v této aplikaci v kódu. Chcete-li toho dosáhnout, vytvořte nový <xref:System.Windows.ResourceDictionary> instance a všechny prostředky přidat do slovníku pomocí následná volání <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>. Potom použijte <xref:System.Windows.ResourceDictionary> proto vytvoří nastavit <xref:System.Windows.FrameworkElement.Resources%2A> vlastnost na element, který se nachází v oboru stránky, nebo <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>. Můžete také zachovat <xref:System.Windows.ResourceDictionary> jako samostatný objekt bez jeho přidání do elementu. Ale pokud to uděláte, můžete musí přístup k prostředkům v rámci něj klíčem položky, jako by šlo generický slovník. A <xref:System.Windows.ResourceDictionary> , který není připojen k elementu `Resources` vlastnost nebude existovat jako součást strom prvku a nemá žádný obor v pořadí vyhledávání, které mohou být využívána <xref:System.Windows.FrameworkElement.FindResource%2A> a související metody.  
  
<a name="objectaskey"></a>   
## <a name="using-objects-as-keys"></a>Použití objektů jako klíče  
 Většina použití prostředků nastaví klíč prostředku bude řetězec. Ale různé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce záměrně nepoužívejte řetězec typu k určení klíče, místo tohoto parametru je objekt. Funkce s prostředků s klíči objektu používá [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podpora styl a motiv. Každý styly motivů, které se stanou výchozího stylu pro ovládací prvek jinak než stylem jsou klíčovány pomocí <xref:System.Type> ovládacího prvku, který se má použít. Je nastaven podle typu poskytuje spolehlivé vyhledávání mechanismus, který funguje na výchozí instance jednotlivých typech ovládacích prvků a typ jde detekoval reflexe a používat pro používání stylů pro odvozené třídy i v případě, že odvozený typ, jinak nemá žádný výchozí styl. Můžete zadat <xref:System.Type> klíč pro prostředek definovaný v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pomocí [x: Type – rozšíření značek](../../xaml-services/x-type-markup-extension.md). Podobně jako rozšíření existovat pro další použití klíče neřetězcový, které podporují [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce, jako [– rozšíření značek ComponentResourceKey](componentresourcekey-markup-extension.md).  
  
## <a name="see-also"></a>Viz také:
- [Prostředky XAML](xaml-resources.md)
- [Styly a šablony](../controls/styling-and-templating.md)
