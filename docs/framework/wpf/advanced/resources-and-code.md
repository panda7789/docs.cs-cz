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
ms.openlocfilehash: 3d504467c137c1e3f494e120217957661f4e75a3
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458754"
---
# <a name="resources-and-code"></a>Zdroje a kód
Tento přehled se zaměřuje na to, jak je možné k prostředkům [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] přistupovat nebo vytvořit pomocí kódu místo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] syntaxe. Další informace o obecném využití prostředků a prostředcích [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] perspektivě syntaxe najdete v tématu [prostředky XAML](xaml-resources.md).  

<a name="accessing"></a>   
## <a name="accessing-resources-from-code"></a>Přístup k prostředkům z kódu  
 Klíče, které identifikují prostředky, pokud jsou definovány pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jsou také použity k načtení konkrétních prostředků, pokud požadujete prostředek v kódu. Nejjednodušší způsob, jak načíst prostředek z kódu, je volat buď <xref:System.Windows.FrameworkElement.FindResource%2A>, nebo metodu <xref:System.Windows.FrameworkElement.TryFindResource%2A> z objektů na úrovni architektury ve vaší aplikaci. Rozdíl mezi těmito metodami spočívá v situaci, kdy požadovaný klíč nebyl nalezen. <xref:System.Windows.FrameworkElement.FindResource%2A> vyvolá výjimku. <xref:System.Windows.FrameworkElement.TryFindResource%2A> nevyvolá výjimku, ale vrátí `null`. Každá metoda bere klíč prostředku jako vstupní parametr a vrací volně typované objekty. Klíč prostředku je obvykle řetězec, ale existují občasné neřetězcové využití. Podrobnosti najdete v části [použití objektů jako klíčů](#objectaskey) . Obvykle byste přetypování vráceného objektu na typ vyžadovaný vlastností, kterou nastavujete při vyžádání prostředku. Logika vyhledávání pro překlad prostředku kódu je stejná jako odkaz na dynamický prostředek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] případ. Hledání prostředků začíná volajícím elementem a pak pokračuje v následných nadřazených prvcích v logickém stromu. Vyhledávání v případě potřeby pokračuje dále v prostředcích prostředků aplikace, v motivech a systémových prostředků. Požadavek kódu na prostředek bude správně fungovat za běhu ve slovnících pro změny v modulech prostředků, které mohly být provedeny po načtení slovníku prostředků z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]a také pro změny systémových prostředků v reálném čase.  
  
 Následuje stručný příklad kódu, který nalezne prostředek podle klíče a použije vrácenou hodnotu k nastavení vlastnosti implementované jako obslužná rutina události <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
 [!code-csharp[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#resourceproceduralget)]
 [!code-vb[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#resourceproceduralget)]  
  
 Alternativní metoda pro přiřazení odkazu na prostředek je <xref:System.Windows.FrameworkElement.SetResourceReference%2A>. Tato metoda přijímá dva parametry: klíč prostředku a identifikátor pro konkrétní vlastnost závislosti, která je přítomna v instanci elementu, do které má být přiřazena hodnota prostředku. Funkčně je tato metoda stejná a má výhodu, že není potřeba přetypování vrácených hodnot.  
  
 Ještě jiný způsob, jak přistupovat k prostředkům programově, je přístup k obsahu vlastnosti <xref:System.Windows.FrameworkElement.Resources%2A> jako slovník. Přístup ke slovníku obsaženému v této vlastnosti je také způsob, jakým můžete přidat nové prostředky do existujících kolekcí. Zkontrolujte, zda je daný název klíče již v kolekci zabraný, a další operace se slovníkem a kolekcí. Pokud píšete [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace zcela v kódu, můžete také vytvořit celou kolekci v kódu, přiřadit k ní klíče a poté přiřadit dokončenou kolekci k vlastnosti <xref:System.Windows.FrameworkElement.Resources%2A> zavedeného prvku. Tato akce bude popsána v následující části.  
  
 V rámci libovolné <xref:System.Windows.FrameworkElement.Resources%2A> kolekce se můžete indexovat pomocí konkrétního klíče jako indexu, ale měli byste si uvědomit, že přístup k prostředku tímto způsobem nedodržuje normální běhová pravidla překladu prostředků. Přistupujete pouze k této konkrétní kolekci. Vyhledávání prostředků neprojde oborem do kořenového adresáře nebo aplikace, pokud v požadovaném klíči nebyl nalezen žádný platný objekt. Tento přístup ale může mít v některých případech vliv na výkon, protože rozsah hledání klíče je více omezený. Další informace o tom, jak pracovat s slovníkem prostředků, najdete v tématu Třída <xref:System.Windows.ResourceDictionary>.  
  
<a name="creating"></a>   
## <a name="creating-resources-with-code"></a>Vytváření prostředků s kódem  
 Pokud chcete vytvořit celou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikaci v kódu, můžete také v kódu vytvořit jakékoli prostředky v této aplikaci. Dosáhnete toho tak, že vytvoříte novou instanci <xref:System.Windows.ResourceDictionary> a potom do slovníku přidáte všechny prostředky pomocí následných volání, která <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>. Pak použijte <xref:System.Windows.ResourceDictionary> takto vytvořen k nastavení vlastnosti <xref:System.Windows.FrameworkElement.Resources%2A> u prvku, který se nachází v rozsahu stránky, nebo <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>. Můžete také zachovat <xref:System.Windows.ResourceDictionary> jako samostatný objekt bez jeho přidání do elementu. Nicméně pokud to uděláte, musíte získat přístup k prostředkům, které jsou v něm v rámci klíče položky, jako by šlo o obecný slovník. <xref:System.Windows.ResourceDictionary>, která není připojena k elementu `Resources` vlastnost neexistují jako součást stromové struktury elementů a ve vyhledávací sekvenci neexistuje rozsah, který lze použít <xref:System.Windows.FrameworkElement.FindResource%2A> a související metody.  
  
<a name="objectaskey"></a>   
## <a name="using-objects-as-keys"></a>Použití objektů jako klíčů  
 Většina využití prostředků nastaví klíč prostředku jako řetězec. Nicméně různé funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] záměrně nepoužívají typ řetězce k zadání klíčů, ale tento parametr je objekt. Schopnost, že se prostředek bude používat objektem, se používá ve stylu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a podpora. Styly v motivech, které se stanou výchozím stylem pro jiný ovládací prvek bez stylu, jsou každou klíčem <xref:System.Type> ovládacího prvku, na který by se měly vztahovat. Se zachováním pomocí typu poskytuje spolehlivý vyhledávací mechanismus, který pracuje na výchozích instancích každého typu ovládacího prvku a typ lze detekovat reflexí a použitým pro styly odvozených tříd, i když odvozený typ jinak nemá žádný výchozí styl. Můžete zadat <xref:System.Type> klíč pro prostředek definovaný v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pomocí [rozšíření značek x:Type](../../xaml-services/x-type-markup-extension.md). Podobná rozšíření existují pro další použití neřetězcových klíčů, která podporují funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], jako je například [rozšíření značek ComponentResourceKey](componentresourcekey-markup-extension.md).  
  
## <a name="see-also"></a>Viz také:

- [Prostředky XAML](xaml-resources.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
