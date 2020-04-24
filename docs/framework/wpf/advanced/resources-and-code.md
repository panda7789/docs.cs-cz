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
ms.openlocfilehash: 8074562ddb865b482cf123743796ac68bb529f85
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646232"
---
# <a name="resources-and-code"></a>Zdroje a kód
Tento přehled se [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zaměřuje na to, jak lze [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] k prostředkům přistupovat nebo je vytvářet pomocí kódu, nikoli syntaxe. Další informace o obecném využití [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] prostředků a prostředky z hlediska syntaxe naleznete v tématu [XAML resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  

<a name="accessing"></a>
## <a name="accessing-resources-from-code"></a>Přístup k prostředkům z kódu  
 Klíče, které identifikují prostředky, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pokud jsou definovány prostřednictvím se také používají k načtení konkrétní prostředky, pokud požadujete prostředek v kódu. Nejjednodušší způsob, jak načíst prostředek z kódu <xref:System.Windows.FrameworkElement.FindResource%2A> je <xref:System.Windows.FrameworkElement.TryFindResource%2A> volání nebo metodu z objektů na úrovni rozhraní ve vaší aplikaci. Behaviorální rozdíl mezi těmito metodami je co se stane, pokud není nalezen požadovaný klíč. <xref:System.Windows.FrameworkElement.FindResource%2A>vysazuje výjimku; <xref:System.Windows.FrameworkElement.TryFindResource%2A> nevyvolá výjimku, `null`ale vrátí . Každá metoda přebírá klíč prostředku jako vstupní parametr a vrací volně zadaný objekt. Klíč prostředku je obvykle řetězec, ale existují příležitostné neřetězcové použití; podrobnosti naleznete v části [Použití objektů jako klíčů.](#objectaskey) Obvykle by přetypování vrácený objekt typu vyžadovanévlastnosti, kterou nastavujete při žádosti o prostředek. Logika vyhledávání pro rozlišení prostředků kódu je stejná jako případ odkazu na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dynamický prostředek. Hledání prostředků začíná od volajícího prvku a potom pokračuje na po sobě jdoucí nadřazené prvky v logickém stromu. Vyhledávání pokračuje dále do aplikačních prostředků, motivů a systémových prostředků v případě potřeby. Požadavek na kód pro prostředek bude správně účet pro změny za běhu ve slovníku prostředků, které by mohly být provedeny po tomto slovníku prostředků načteny z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]aplikace a také pro změny systémových prostředků v reálném čase.  
  
 Následuje stručný příklad kódu, který vyhledá prostředek podle klíče a použije vrácenou <xref:System.Windows.Controls.Primitives.ButtonBase.Click> hodnotu k nastavení vlastnosti implementované jako obslužná rutina události.  
  
 [!code-csharp[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#resourceproceduralget)]
 [!code-vb[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#resourceproceduralget)]  
  
 Alternativní metodou pro přiřazení odkazu <xref:System.Windows.FrameworkElement.SetResourceReference%2A>na prostředek je . Tato metoda má dva parametry: klíč prostředku a identifikátor pro konkrétní vlastnost závislosti, která je k dispozici na instanci prvku, ke kterému by měla být přiřazena hodnota prostředku. Funkčně tato metoda je stejná a má tu výhodu, že nevyžaduje žádné odlévání vrácené hodnoty.  
  
 Dalším způsobem, jak programově přistupovat ke zdrojům, je přístup k obsahu vlastnosti <xref:System.Windows.FrameworkElement.Resources%2A> jako slovníku. Přístup ke slovníku obsažené této vlastnosti je také, jak můžete přidat nové prostředky do existujících kolekcí, zkontrolujte, zda je daný název klíče již přijata v kolekci a další operace slovníku/kolekce. Pokud píšete [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikaci zcela v kódu, můžete také vytvořit celou kolekci v kódu, přiřadit klíče <xref:System.Windows.FrameworkElement.Resources%2A> k němu a pak přiřadit dokončenou kolekci vlastnost zavedeného prvku. To bude popsáno v další části.  
  
 Můžete indexovat v <xref:System.Windows.FrameworkElement.Resources%2A> rámci dané kolekce, pomocí konkrétní klíč jako index, ale měli byste si být vědomi toho, že přístup k prostředku tímto způsobem nedodržuje normální pravidla za běhu rozlišení prostředků. K této konkrétní kolekci přistupujete pouze k této kolekci. Vyhledávání prostředků nebude procházet obor do kořenového adresáře nebo aplikace, pokud nebyl nalezen žádný platný objekt na požadovaný klíč. Tento přístup však může mít výhody výkonu v některých případech právě proto, že rozsah hledání klíče je omezenější. Další <xref:System.Windows.ResourceDictionary> podrobnosti o tom, jak přímo pracovat se slovníkem prostředků, najdete ve třídě.  
  
<a name="creating"></a>
## <a name="creating-resources-with-code"></a>Vytváření prostředků pomocí kódu  
 Pokud chcete vytvořit celou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikaci v kódu, můžete také vytvořit všechny prostředky v této aplikaci v kódu. Chcete-li toho dosáhnout, vytvořte novou <xref:System.Windows.ResourceDictionary> instanci a přidejte <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>všechny prostředky do slovníku pomocí následných volání . Potom použijte <xref:System.Windows.ResourceDictionary> tak to vytvořil <xref:System.Windows.FrameworkElement.Resources%2A> nastavit vlastnost na prvek, který je <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>přítomen v oboru stránky nebo . Můžete také zachovat <xref:System.Windows.ResourceDictionary> jako samostatný objekt bez přidání do prvku. Pokud to však uděláte, musíte přistupovat k prostředkům v něm podle klíče položky, jako by se jednalo o obecný slovník. A, <xref:System.Windows.ResourceDictionary> který není připojen `Resources` k elementu vlastnost by neexistoval jako součást stromu elementu a nemá <xref:System.Windows.FrameworkElement.FindResource%2A> žádný obor ve vyhledávací sekvenci, které lze použít a související metody.  
  
<a name="objectaskey"></a>
## <a name="using-objects-as-keys"></a>Použití objektů jako klíčů  
 Většina využití prostředků nastaví klíč prostředku jako řetězec. Různé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce však záměrně nepoužívají typ řetězce k určení klíčů, místo toho je tento parametr objektem. Schopnost mít prostředek zadávaný objektem je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používán stylem a podporou témat. Styly v <xref:System.Type> motivech, které se stanou výchozím stylem pro jinak nestylizovaný ovládací prvek, jsou zakódovány ovládacím prvkem, na který by se měly vztahovat. Právě keyed podle typu poskytuje spolehlivý vyhledávací mechanismus, který pracuje na výchozí instance každého typu ovládacího prvku a typ může být detekován odrazem a použit pro stylování odvozené třídy, i když odvozený typ jinak nemá výchozí styl. <xref:System.Type> Klíč pro prostředek definovaný v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] písmenu můžete zadat pomocí [rozšíření x:Type Markup Extension](../../../desktop-wpf/xaml-services/xtype-markup-extension.md). Podobná rozšíření existují pro jiné použití neřetězcových klíčů, které podporují [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce, například Rozšíření značek [ComponentResourceKey](componentresourcekey-markup-extension.md).  
  
## <a name="see-also"></a>Viz také

- [Zdroje XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
