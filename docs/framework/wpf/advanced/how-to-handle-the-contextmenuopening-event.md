---
title: 'Postupy: Zpracování události ContextMenuOpening'
ms.date: 03/30/2017
helpviewer_keywords:
- ContextMenuOpening properties [WPF]
ms.assetid: 789652fb-1951-4217-934a-7843e355adf4
ms.openlocfilehash: 65a1e34d5b078c49bf59c2d9787812940c9a7494
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340396"
---
# <a name="how-to-handle-the-contextmenuopening-event"></a>Postupy: Zpracování události ContextMenuOpening
<xref:System.Windows.FrameworkElement.ContextMenuOpening> Události mohou být zpracovány v aplikaci buď upravit existující místní nabídku před zobrazit nebo potlačit v nabídce, která by jinak zobrazit tak, že nastavíte <xref:System.Windows.RoutedEventArgs.Handled%2A> vlastnost `true` v datech události. Typické důvod nastavení <xref:System.Windows.RoutedEventArgs.Handled%2A> k `true` události, data je nahraďte nabídku zcela nový <xref:System.Windows.Controls.ContextMenu> objekt, což v některých případech vyžaduje zrušení operace a spouští se nový otevřít. Při zápisu obslužných rutin pro <xref:System.Windows.FrameworkElement.ContextMenuOpening> události, byste měli vědět o problémy načasování mezi <xref:System.Windows.Controls.ContextMenu> ovládacího prvku a službu, která je zodpovědná za otevření a obecně umístění kontextové nabídky pro ovládací prvky. Toto téma popisuje některé techniky kód pro otevření scénáře různých kontextovou nabídku a ukazuje případ, kde jsou časové potíže vstupu do play.  
  
 Existuje několik scénářů pro zpracování <xref:System.Windows.FrameworkElement.ContextMenuOpening> události:  
  
-   Úprava položek nabídky před zobrazení.  
  
-   Nahradí celý nabídku před zobrazení.  
  
-   Zcela potlačení jakékoliv existující místní nabídky a zobrazování žádné kontextové nabídky.  
  
## <a name="example"></a>Příklad  
  
## <a name="adjusting-the-menu-items-before-display"></a>Úprava položek nabídky před zobrazení  
 Úprava stávající položky nabídky je docela jednoduché a je pravděpodobně nejběžnější scénáře. Můžete tak učinit, aby bylo možné přidávat nebo odebírat kontextové nabídky v reakci na aktuální informace o stavu ve vaší aplikaci nebo konkrétní stav informace, které je k dispozici jako vlastnost v objektu, ve kterém je požadováno v místní nabídce.  
  
 Obecný postup je se dostat zdroj události, která je na určitý ovládací prvek, který bylo kliknuto pravým tlačítkem, a <xref:System.Windows.FrameworkElement.ContextMenu%2A> vlastnost z něj. Obvykle je vhodné zkontrolovat <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekce prohlédnout položky nabídky kontextu již existují v nabídce a pak přidat nebo odebrat odpovídající nové <xref:System.Windows.Controls.MenuItem> položek do nebo z kolekce.  
  
 [!code-csharp[ContextMenuOpeningHandlers#AddItemNoHandle](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#additemnohandle)]  
  
## <a name="replacing-the-entire-menu-before-display"></a>Nahrazování celé nabídku před zobrazení  
 Alternativní scénář je, pokud mají být nahrazeny celou kontextové nabídky. Můžete samozřejmě také použít varianta předcházejícího kódu odebrat všechny položky z existující kontextovou nabídku a přidat nové spuštění s položkou nula. Ale mnohem intuitivnější přístup k nahrazení všech položek v místní nabídce je k vytvoření nového <xref:System.Windows.Controls.ContextMenu>, přidejte do ní položky a pak nastavte <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType> vlastnost ovládacího prvku, který bude nový <xref:System.Windows.Controls.ContextMenu>.  
  
 Tady je kód jednoduchý obslužné rutiny pro nahrazení <xref:System.Windows.Controls.ContextMenu>. Kód odkazuje na vlastní `BuildMenu` metodu, která je oddělená, vzhledem k tomu, že je volána více než jeden příklad obslužné rutiny.  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceNoReopen](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacenoreopen)]  
  
 [!code-csharp[ContextMenuOpeningHandlers#BuildMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#buildmenu)]  
  
 Ale pokud použijete tento styl obslužné rutiny pro <xref:System.Windows.FrameworkElement.ContextMenuOpening>, může potenciálně vystavit časování, pokud objekt, kde nastavujete <xref:System.Windows.Controls.ContextMenu> nemá stávající místní nabídka. Když uživatel klepne pravým tlačítkem myši ovládací prvek <xref:System.Windows.FrameworkElement.ContextMenuOpening> dojde i v případě existující <xref:System.Windows.Controls.ContextMenu> je prázdná nebo null. Ale v takovém případě cokoli, co nového <xref:System.Windows.Controls.ContextMenu> nastavíte na zdroji element dorazí pozdě má být zobrazen. Také, pokud uživatel se stane, klikněte pravým tlačítkem myši druhém, v tuto chvíli nové <xref:System.Windows.Controls.ContextMenu> se zobrazí, je hodnota není null, a vaše obslužná rutina správně, nahradí a zobrazit v nabídce, pokud obslužná rutina se spustí jednou. To naznačuje dvě možná řešení:  
  
1. – Pomáhat zajistit, že <xref:System.Windows.FrameworkElement.ContextMenuOpening> obslužné rutiny vždy spouštějte ovládací prvky, které mají alespoň zástupný symbol <xref:System.Windows.Controls.ContextMenu> k dispozici, který chcete nahradit kód obslužné rutiny. V takovém případě můžete dál používat rutiny uvedené v předchozím příkladu, ale obvykle chcete přiřadit zástupný symbol <xref:System.Windows.Controls.ContextMenu> v počáteční značky:  
  
     [!code-xaml[ContextMenuOpeningHandlers#XAMLWithInitCM](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml#xamlwithinitcm)]  
  
2. Předpokládejme, že počáteční <xref:System.Windows.Controls.ContextMenu> může být hodnota null, na základě nějaké logiky předběžné. Můžete buď zaškrtnout <xref:System.Windows.Controls.ContextMenu> minimálně jednou pro hodnotu null, nebo použijte příznak ve vašem kódu ke kontrole, jestli vaše obslužná rutina byla spuštěna. Vzhledem k tomu, že budete předpokládat, že <xref:System.Windows.Controls.ContextMenu> je o bude zobrazena, vaše obslužná rutina pak nastaví <xref:System.Windows.RoutedEventArgs.Handled%2A> k `true` v datech události. K <xref:System.Windows.Controls.ContextMenuService> , který je zodpovědný za kontextové nabídky zobrazení, `true` hodnota <xref:System.Windows.RoutedEventArgs.Handled%2A> události dat představuje požadavek na zrušení zobrazení místní nabídky / řízení kombinaci, která vyvolala událost.  
  
 Teď, když jste předtím potlačili potenciálně podezřelých kontextové nabídky, dalším krokem je zadat novou a potom zobrazit. Nastavení nové jeden je v podstatě, stejný jako předchozí obslužnou rutinou: vytvoříte nový <xref:System.Windows.Controls.ContextMenu> a nastavit zdroj ovládacího prvku <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType> vlastnost s ním. Další krok je, že teď musíte vynutit zobrazení místní nabídky, protože potlačení první pokus o. Chcete-li vynutit zobrazení, nastavte <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A?displayProperty=nameWithType> vlastnost `true` v rámci obslužné rutiny. Buďte opatrní při tomto, protože otevření místní nabídky v obslužné rutině vyvolá <xref:System.Windows.FrameworkElement.ContextMenuOpening> události znovu. Můžete znovu zadat vaše obslužná rutina, stane se takový neomezeně rekurzivní. To je důvod, proč je potřeba vždy zkontrolujte `null` nebo použijte příznak-li otevřít místní nabídku v rámci <xref:System.Windows.FrameworkElement.ContextMenuOpening> obslužné rutiny události.  
  
## <a name="suppressing-any-existing-context-menu-and-displaying-no-context-menu"></a>Potlačení jakékoliv existující místní nabídky a žádné kontextové nabídky zobrazení  
 Poslední scénář zápis obslužné rutiny, které potlačí nabídky úplně neobvyklé. Pokud daný ovládací prvek by se nemělo zobrazení místní nabídky, zajistit tím, než potlačení v nabídce, stačí, když si uživatel vyžádá, se pravděpodobně vhodnější způsoby. Ale pokud chcete použít obslužnou rutinu potlačit kontextovou nabídku a zobrazit nic, pak by měl vaše obslužná rutina stačí nastavit <xref:System.Windows.RoutedEventArgs.Handled%2A> k `true` v datech události. <xref:System.Windows.Controls.ContextMenuService> , Která zodpovídá za zobrazení místní nabídky bude kontrolovat data události z události vyvolané na ovládací prvek. Pokud byla označena jako událost <xref:System.Windows.RoutedEventArgs.Handled%2A> kdekoli na trase pak otevřít akce kontextu nabídky, který spustil danou událost je potlačeno.  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceReopen](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacereopen)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.ContextMenu>
- <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType>
- [Přehled základních elementů](base-elements-overview.md)
- [ContextMenu – přehled](../controls/contextmenu-overview.md)
