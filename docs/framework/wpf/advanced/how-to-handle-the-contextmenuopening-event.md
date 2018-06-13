---
title: 'Postupy: Zpracování události ContextMenuOpening'
ms.date: 03/30/2017
helpviewer_keywords:
- ContextMenuOpening properties [WPF]
ms.assetid: 789652fb-1951-4217-934a-7843e355adf4
ms.openlocfilehash: ab4c4867981cd318738b7404d76f2f5932bb9059
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547482"
---
# <a name="how-to-handle-the-contextmenuopening-event"></a>Postupy: Zpracování události ContextMenuOpening
<xref:System.Windows.FrameworkElement.ContextMenuOpening> Události lze zpracovat v aplikaci buď upravit existující kontextové nabídky před zobrazit nebo potlačit v nabídce, která by jinak zobrazí nastavením <xref:System.Windows.RoutedEventArgs.Handled%2A> vlastnost `true` v datech události. Typické důvod nastavení <xref:System.Windows.RoutedEventArgs.Handled%2A> k `true` události dat je nahradit nabídku zcela nový <xref:System.Windows.Controls.ContextMenu> objektu, který někdy vyžaduje zrušení operace a spuštění nové otevřete. Pokud píšete obslužné rutiny pro <xref:System.Windows.FrameworkElement.ContextMenuOpening> událostí, byste měli vědět o problémy načasování mezi <xref:System.Windows.Controls.ContextMenu> řízení a službou, která je odpovědná za otevírání a obecně umístění kontextové nabídky pro ovládací prvky. Toto téma popisuje některé techniky kódu pro různé kontextovou nabídku otevírání scénáře a znázorňuje případ kterých časové potíže pocházejí do play.  
  
 Existuje několik situací pro zpracování <xref:System.Windows.FrameworkElement.ContextMenuOpening> událostí:  
  
-   Úprava položek nabídky před zobrazení.  
  
-   Nahraďte celou nabídky před zobrazení.  
  
-   Zcela potlačit jakékoli existující kontextovou nabídku a zobrazení žádné kontextové nabídky.  
  
## <a name="example"></a>Příklad  
  
## <a name="adjusting-the-menu-items-before-display"></a>Úprava položek nabídky před zobrazení  
 Úprava stávající položky nabídky je docela jednoduchá a je pravděpodobně nejběžnější scénář. Můžete tak učinit, aby bylo možné přidat nebo odstranit možnosti kontextové nabídky v reakci na aktuální informace o stavu ve vaší aplikaci nebo informace o konkrétní stavu, která je k dispozici jako vlastnost v objektu, kde je vyžadován v místní nabídce.  
  
 Obecné technika je získat zdroj události, který je konkrétní ovládací prvek, který byl klepli pravým tlačítkem myši, a získat <xref:System.Windows.FrameworkElement.ContextMenu%2A> vlastnost z něj. Obvykle je vhodné zkontrolovat <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekce zobrazíte jaké položek kontextové nabídky již existují v nabídce a potom přidat nebo odebrat příslušné nové <xref:System.Windows.Controls.MenuItem> položek do nebo z kolekce.  
  
 [!code-csharp[ContextMenuOpeningHandlers#AddItemNoHandle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#additemnohandle)]  
  
## <a name="replacing-the-entire-menu-before-display"></a>Nahraďte celou nabídky před zobrazení  
 Alternativní scénář je, pokud chcete nahradit celý kontextové nabídky. Samozřejmě může také použít varianta předchozí kód odebrat každá položka existující kontextovou nabídku a přidat nové spuštění s položkou nula. Ale intuitivnější přístup k nahrazení všechny položky v místní nabídce vytvořte novou <xref:System.Windows.Controls.ContextMenu>, přidejte do ní položky a potom nastavte <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType> vlastností ovládacího prvku jako nový <xref:System.Windows.Controls.ContextMenu>.  
  
 Tady je kód jednoduché obslužné rutiny pro náhradu <xref:System.Windows.Controls.ContextMenu>. Kód odkazuje na vlastní `BuildMenu` metodu, která je oddělená out vzhledem k tomu, že se označuje jako více než jeden příklad obslužné rutiny.  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceNoReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacenoreopen)]  
  
 [!code-csharp[ContextMenuOpeningHandlers#BuildMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#buildmenu)]  
  
 Ale pokud použijete tento styl obslužné rutiny pro <xref:System.Windows.FrameworkElement.ContextMenuOpening>, časové potíže mohou potenciálně odhalit, pokud objekt, kde nastavujete <xref:System.Windows.Controls.ContextMenu> nemá dříve existující místní nabídce. Když uživatel klikne pravým tlačítkem myši ovládací prvek <xref:System.Windows.FrameworkElement.ContextMenuOpening> se vyvolá, i když existující <xref:System.Windows.Controls.ContextMenu> je prázdná nebo null. Ale v takovém případě ať nové <xref:System.Windows.Controls.ContextMenu> nastavíte na zdroji element dorazí příliš pozdní, který se má zobrazit. Navíc pokud uživatel se stane ještě jednou klikněte pravým tlačítkem myši, v tuto chvíli nové <xref:System.Windows.Controls.ContextMenu> se zobrazí, je hodnota jinou hodnotu null, a správně nahradí a zobrazovat v nabídce, když obslužná rutina se spustí podruhé vaší obslužné rutiny. To naznačuje dvě možná řešení:  
  
1.  Zajistěte, <xref:System.Windows.FrameworkElement.ContextMenuOpening> obslužné rutiny vždy spouštění ovládací prvky, které mají alespoň zástupný symbol <xref:System.Windows.Controls.ContextMenu> k dispozici, které máte v úmyslu nahrazuje kód obslužné rutiny. V takovém případě můžete dál používat obslužná rutina ukazuje předchozí příklad, ale obvykle chcete přiřadit zástupný symbol <xref:System.Windows.Controls.ContextMenu> do počáteční kódu:  
  
     [!code-xaml[ContextMenuOpeningHandlers#XAMLWithInitCM](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml#xamlwithinitcm)]  
  
2.  Předpokládáme, že počáteční <xref:System.Windows.Controls.ContextMenu> hodnota může být null, na základě některé předběžné logiky. Může buď kontrola <xref:System.Windows.Controls.ContextMenu> pro hodnotu null, nebo použijte příznak ve vašem kódu zkontrolujte, zda má ke vaší obslužné rutiny spustit alespoň jednou. Protože můžete předpokládat, že <xref:System.Windows.Controls.ContextMenu> je o být zobrazeny, vaší obslužné rutiny a nastaví <xref:System.Windows.RoutedEventArgs.Handled%2A> k `true` v datech události. K <xref:System.Windows.Controls.ContextMenuService> který zodpovídá za zobrazení kontextové nabídky, `true` hodnota <xref:System.Windows.RoutedEventArgs.Handled%2A> události dat představuje požadavek na zrušení zobrazení místní nabídky / ovládací kombinaci, která vyvolala událost.  
  
 Teď, když jste předtím potlačili potenciálně podezřelou kontextové nabídky, dalším krokem je zadat novou, pak se zobrazí. Nastavení nové jeden je stejný jako předchozí obslužná rutina: vytvoříte novou <xref:System.Windows.Controls.ContextMenu> a nastavte zdroj ovládacího prvku <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType> vlastnost s ním. Další krok je musíte teď vynutit zobrazení v místní nabídce, protože potlačena první pokus o. Chcete-li vynutit zobrazení, nastavíte <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A?displayProperty=nameWithType> vlastnost `true` v rámci obslužná rutina. Buďte opatrní při tomto, protože otevřete kontextu nabídku v obslužné rutině vyvolá <xref:System.Windows.FrameworkElement.ContextMenuOpening> událostí znovu. Pokud je znovu zadat vaší obslužné rutiny, stane se nekonečnou rekurzivní. To je důvod, proč je vždy nutné kontrolovat `null` nebo použijte příznak otevřete z kontextové nabídky z uvnitř <xref:System.Windows.FrameworkElement.ContextMenuOpening> obslužné rutiny události.  
  
## <a name="suppressing-any-existing-context-menu-and-displaying-no-context-menu"></a>Potlačit jakékoli existující kontextovou nabídku a zobrazování žádné kontextové nabídky  
 Je posledním scénáři zápis obslužné rutiny, které potlačí nabídky úplně, neobvyklé. Pokud daný ovládací prvek nemá zobrazíte z kontextové nabídky, způsoby pravděpodobně vhodnější, aby zajistil to než podle potlačení v nabídce jenom v případě, že uživatel požaduje. Ale pokud chcete použít k potlačení z kontextové nabídky a zobrazit nic obslužná rutina, pak by měl vaší obslužné rutiny jednoduše nastavit <xref:System.Windows.RoutedEventArgs.Handled%2A> k `true` v datech události. <xref:System.Windows.Controls.ContextMenuService> Který zodpovídá za zobrazení z kontextové nabídky zkontroluje data události událost je aktivována v ovládacím prvku. Pokud byla označena jako událost <xref:System.Windows.RoutedEventArgs.Handled%2A> kdekoli na trase pak otevřete akci kontextu nabídky, která iniciované událost potlačeno.  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacereopen)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.ContextMenu>  
 <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType>  
 [Přehled základních elementů](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [ContextMenu – přehled](../../../../docs/framework/wpf/controls/contextmenu-overview.md)
