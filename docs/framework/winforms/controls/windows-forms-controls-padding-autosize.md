---
title: Rozvrhnout ovládací prvky s odsazením, okraji a vlastností AutoSize
ms.date: 03/30/2017
f1_keywords:
- Margin.Bottom
- Margin.Left
- Margin.Top
- Margin.All
- Margin.Right
helpviewer_keywords:
- Margin property [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], layout
- AutoSize property [Windows Forms], walkthroughs
- Padding property [Windows Forms], walkthroughs
- layout [Windows Forms], margins and padding
- Windows Forms, layout
ms.assetid: f8ae2a6b-db13-4630-8e25-d104091205c7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ca7942c04434592f2541252c47ac3dd17e03dbac
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742372"
---
# <a name="walkthrough-lay-out-controls-with-padding-margins-and-the-autosize-property"></a>Návod: rozvrhnout ovládací prvky s odsazením, okraji a vlastností AutoSize

Přesné umístění ovládacích prvků ve formuláři je velmi prioritní pro mnoho aplikací. **Návrhář formulářů** v aplikaci Visual Studio poskytuje mnoho nástrojů pro rozložení, které by to bylo možné provést. Tři nejdůležitější jsou vlastnosti <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Control.Padding%2A>a <xref:System.Windows.Forms.Control.AutoSize%2A>, které jsou k dispozici ve všech model Windows Formsch ovládacích prvcích.

Vlastnost <xref:System.Windows.Forms.Control.Margin%2A> definuje prostor kolem ovládacího prvku, který uchovává jiné ovládací prvky o určenou vzdálenost od ohraničení ovládacího prvku.

Vlastnost <xref:System.Windows.Forms.Control.Padding%2A> definuje prostor uvnitř ovládacího prvku, který udržuje obsah ovládacího prvku (například hodnotu vlastnosti <xref:System.Windows.Forms.Control.Text%2A>) o určenou vzdálenost od ohraničení ovládacího prvku.

Následující obrázek ukazuje vlastnosti <xref:System.Windows.Forms.Control.Padding%2A> a <xref:System.Windows.Forms.Control.Margin%2A> ovládacího prvku.

![Odsazení a okraj pro ovládací prvky model Windows Forms](./media/vs-winformpadmargin.gif)

Vlastnost <xref:System.Windows.Forms.Control.AutoSize%2A> dává ovládacím prvkům automatickou velikost obsahu. Velikost se nemění tak, aby byla menší než hodnota původní <xref:System.Windows.Forms.Control.Size%2A> vlastnosti a bude se považovat za hodnotu její vlastnosti <xref:System.Windows.Forms.Control.Padding%2A>.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto Názorného postupu budete potřebovat Visual Studio.

## <a name="create-the-project"></a>Vytvoření projektu

1. V aplikaci Visual Studio vytvořte projekt **aplikace pro Windows** s názvem `LayoutExample`.

2. Vyberte formulář v **Návrhář formulářů**.

## <a name="set-margins-for-controls"></a>Nastavit okraje pro ovládací prvky

Výchozí vzdálenost mezi ovládacími prvky můžete nastavit pomocí vlastnosti <xref:System.Windows.Forms.Control.Margin%2A>. Když přesunete ovládací prvek dostatečně blízko k jinému ovládacímu prvku, zobrazí se snapline, který zobrazuje okraje pro tyto dva ovládací prvky. Ovládací prvek, který přesouváte, bude také přichycený ke vzdálenosti definované okraji.

### <a name="arrange-controls-on-your-form-using-the-margin-property"></a>Uspořádání ovládacích prvků na formuláři pomocí vlastnosti okraj

1. Přetáhněte ze sady **nástrojů** do formuláře dva ovládací prvky <xref:System.Windows.Forms.Button>.

2. Vyberte jeden z ovládacích prvků <xref:System.Windows.Forms.Button> a přesuňte ho blízko k druhému, dokud nebudou skoro dotek.

   Sledujte snapline, která se mezi nimi nacházejí. Tato vzdálenost je součtem dvou <xref:System.Windows.Forms.Control.Margin%2A> hodnot ovládacích prvků. Ovládací prvek, na který se přesouváte, se přitahuje na tuto vzdálenost. Podrobnosti najdete v tématu [Návod: uspořádání ovládacích prvků na model Windows Forms pomocí zarovnávacím čárám](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).

3. Změňte vlastnost <xref:System.Windows.Forms.Control.Margin%2A> jednoho z ovládacích prvků rozbalením položky <xref:System.Windows.Forms.Control.Margin%2A> v okně **vlastnosti** a nastavením vlastnosti <xref:System.Windows.Forms.Padding.All%2A> na hodnotu **20**.

4. Vyberte jeden z ovládacích prvků <xref:System.Windows.Forms.Button> a přesuňte ho blízko k druhému.

   SnapLine definující součet hodnot okrajů je delší a ovládací prvek se přitahuje na větší vzdálenost od druhého ovládacího prvku.

5. Rozbalením položky <xref:System.Windows.Forms.Control.Margin%2A> v okně **vlastnosti** změňte vlastnost <xref:System.Windows.Forms.Control.Margin%2A> vybraného ovládacího prvku a nastavte vlastnost <xref:System.Windows.Forms.Padding.Top%2A> na hodnotu **5**.

6. Přesuňte vybraný ovládací prvek pod druhým ovládacím prvkem a sledujte, zda je snapline kratší. Přesuňte vybraný ovládací prvek nalevo od druhého ovládacího prvku a sledujte, že snapline zachovává hodnotu zjištěnou v kroku 4.

7. Můžete nastavit všechny aspekty vlastnosti <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Padding.Left%2A>, <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Right%2A>, <xref:System.Windows.Forms.Padding.Bottom%2A>, na jiné hodnoty, nebo je můžete nastavit na stejnou hodnotu s vlastností <xref:System.Windows.Forms.Padding.All%2A>.

## <a name="set-padding-for-controls"></a>Nastavit odsazení pro ovládací prvky

Chcete-li dosáhnout přesného rozložení požadovaného pro aplikaci, ovládací prvky budou často obsahovat podřízené ovládací prvky. Pokud chcete určit blízkost okraje podřízeného ovládacího prvku na hranici nadřazeného ovládacího prvku, použijte vlastnost <xref:System.Windows.Forms.Control.Padding%2A> nadřazeného ovládacího prvku ve spojení s vlastností <xref:System.Windows.Forms.Control.Margin%2A> podřízeného ovládacího prvku. Vlastnost <xref:System.Windows.Forms.Control.Padding%2A> slouží také k řízení blízkosti obsahu ovládacího prvku (například vlastnost <xref:System.Windows.Forms.Control.Text%2A> ovládacího prvku <xref:System.Windows.Forms.Button>) na jeho ohraničení.

### <a name="arrange-controls-on-your-form-using-padding"></a>Uspořádání ovládacích prvků na formuláři pomocí odsazení

1. Přetáhněte ovládací prvek <xref:System.Windows.Forms.Button> z **panelu nástrojů** do formuláře.

2. Změňte hodnotu vlastnosti <xref:System.Windows.Forms.Control.AutoSize%2A> ovládacího prvku <xref:System.Windows.Forms.Button> na **hodnotu true**.

3. Rozbalením položky <xref:System.Windows.Forms.Control.Padding%2A> v okně **vlastnosti** změňte vlastnost <xref:System.Windows.Forms.Control.Padding%2A> a nastavte vlastnost <xref:System.Windows.Forms.Padding.All%2A> na hodnotu **5**.

   Ovládací prvek se rozšíří a poskytne prostor pro nové odsazení.

4. Přetáhněte ovládací prvek <xref:System.Windows.Forms.GroupBox> z **panelu nástrojů** do formuláře. Přetáhněte ovládací prvek <xref:System.Windows.Forms.Button> z **panelu nástrojů** do ovládacího prvku <xref:System.Windows.Forms.GroupBox>. Umístěte ovládací prvek <xref:System.Windows.Forms.Button> tak, aby byl vyprázdněn v pravém dolním rohu ovládacího prvku <xref:System.Windows.Forms.GroupBox>.

   Sledujte zarovnávacím čárám, který se zobrazí jako ovládací prvek <xref:System.Windows.Forms.Button> přistupuje k dolnímu a pravému okraji ovládacího prvku <xref:System.Windows.Forms.GroupBox>. Tyto zarovnávacím čárám odpovídají vlastnosti <xref:System.Windows.Forms.Control.Margin%2A> <xref:System.Windows.Forms.Button>.

5. Rozbalením položky <xref:System.Windows.Forms.Control.Padding%2A> v okně **vlastnosti** změňte vlastnost <xref:System.Windows.Forms.Control.Padding%2A> ovládacího prvku <xref:System.Windows.Forms.GroupBox> a nastavte vlastnost <xref:System.Windows.Forms.Padding.All%2A> na hodnotu **20**.

6. Vyberte ovládací prvek <xref:System.Windows.Forms.Button> v rámci <xref:System.Windows.Forms.GroupBox> ovládacího prvku a přesuňte ho směrem do středu <xref:System.Windows.Forms.GroupBox>.

   Zarovnávacím čárám se zobrazí ve větší vzdálenosti od ohraničení ovládacího prvku <xref:System.Windows.Forms.GroupBox>. Tato vzdálenost je součtem vlastnosti <xref:System.Windows.Forms.Control.Margin%2A> ovládacího prvku <xref:System.Windows.Forms.Button> a vlastnosti <xref:System.Windows.Forms.Control.Padding%2A> ovládacího prvku <xref:System.Windows.Forms.GroupBox>.

## <a name="size-controls-automatically"></a>Nastavit velikost ovládacích prvků automaticky

V některých aplikacích nebude velikost ovládacího prvku stejná v době běhu, protože byla v době návrhu. Text ovládacího prvku <xref:System.Windows.Forms.Button> může být například z databáze převeden a jeho délka není známa předem.

Je-li vlastnost <xref:System.Windows.Forms.Control.AutoSize%2A> nastavena na hodnotu `true`, změní se ovládací prvek na jeho obsah. Další informace naleznete v tématu [Přehled vlastností AutoSize](autosize-property-overview.md).

### <a name="arrange-controls-on-your-form-using-the-autosize-property"></a>Uspořádání ovládacích prvků ve formuláři pomocí vlastnosti AutoSize

1. Přetáhněte ovládací prvek <xref:System.Windows.Forms.Button> z **panelu nástrojů** do formuláře.

2. Změňte hodnotu vlastnosti <xref:System.Windows.Forms.Control.AutoSize%2A> ovládacího prvku <xref:System.Windows.Forms.Button> na **hodnotu true**.

3. Změňte vlastnost <xref:System.Windows.Forms.Control.Text%2A> ovládacího prvku <xref:System.Windows.Forms.Button> na **Toto tlačítko má dlouhý řetězec pro jeho vlastnost text**.

   Když změnu potvrdíte, ovládací prvek <xref:System.Windows.Forms.Button> změní velikost sebe sama tak, aby odpovídala novému textu.

4. Přetáhněte jiný ovládací prvek <xref:System.Windows.Forms.Button> z **panelu nástrojů** do formuláře.

5. Změňte vlastnost <xref:System.Windows.Forms.Control.Text%2A> ovládacího prvku <xref:System.Windows.Forms.Button> na "**Toto tlačítko má dlouhý řetězec pro jeho vlastnost text.** "

   Při potvrzení změny se ovládací prvek <xref:System.Windows.Forms.Button> sám nemění a text bude oříznutý pravým okrajem ovládacího prvku.

6. Rozbalením položky <xref:System.Windows.Forms.Control.Padding%2A> v okně **vlastnosti** změňte vlastnost <xref:System.Windows.Forms.Control.Padding%2A> a nastavte vlastnost <xref:System.Windows.Forms.Padding.All%2A> na hodnotu **5**.

   Text v vnitřku ovládacího prvku se ořízne na všech čtyřech stranách.

7. Změňte vlastnost <xref:System.Windows.Forms.Control.AutoSize%2A> ovládacího prvku <xref:System.Windows.Forms.Button> na **hodnotu true**.

   Ovládací prvek <xref:System.Windows.Forms.Button> změní velikost sebe sama tak, aby zahrnovala celý řetězec. Kolem textu bylo přidáno také odsazení, což způsobuje, že se ovládací prvek <xref:System.Windows.Forms.Button> rozbalí do všech čtyř směrů.

8. Přetáhněte ovládací prvek <xref:System.Windows.Forms.Button> z **panelu nástrojů** do formuláře. Umístěte ho poblíž pravého dolního rohu formuláře.

9. Změňte hodnotu vlastnosti <xref:System.Windows.Forms.Control.AutoSize%2A> ovládacího prvku <xref:System.Windows.Forms.Button> na **hodnotu true**.

10. Nastavte vlastnost <xref:System.Windows.Forms.Control.Anchor%2A> ovládacího prvku <xref:System.Windows.Forms.Button> na <xref:System.Windows.Forms.AnchorStyles.Right><xref:System.Windows.Forms.AnchorStyles.Bottom>.

11. Změňte vlastnost <xref:System.Windows.Forms.Control.Text%2A> ovládacího prvku <xref:System.Windows.Forms.Button> na "**Toto tlačítko má dlouhý řetězec pro jeho vlastnost text.** "

   Když změnu potvrdíte, ovládací prvek <xref:System.Windows.Forms.Button> změní velikost směrem doleva. Obecně platí, že Automatická změna velikosti zvětší velikost ovládacího prvku v opačném směru jako jeho nastavení vlastnosti <xref:System.Windows.Forms.Control.Anchor%2A>.

## <a name="autosize-and-autosizemode-properties"></a>Vlastnosti AutoSize a AutoSizeMode

 Některé ovládací prvky podporují vlastnost `AutoSizeMode`, která poskytuje přesnější kontrolu nad chováním automatického přizpůsobení velikosti ovládacího prvku.

### <a name="use-the-autosizemode-property"></a>Použití vlastnosti AutoSizeMode

1. Přetáhněte ovládací prvek <xref:System.Windows.Forms.Panel> z **panelu nástrojů** do formuláře.

2. Nastavte hodnotu vlastnosti <xref:System.Windows.Forms.Control.AutoSize%2A> ovládacího prvku <xref:System.Windows.Forms.Panel> na **hodnotu true**.

3. Přetáhněte ovládací prvek <xref:System.Windows.Forms.Button> z **panelu nástrojů** do ovládacího prvku <xref:System.Windows.Forms.Panel>.

4. Ovládací prvek <xref:System.Windows.Forms.Button> umístit poblíž pravého dolního rohu ovládacího prvku <xref:System.Windows.Forms.Panel>.

5. Vyberte ovládací prvek <xref:System.Windows.Forms.Panel> a přitáhněte k úchytu pravého dolního úchytu. Změňte velikost ovládacího prvku <xref:System.Windows.Forms.Panel> tak, aby byl větší a menší.

   > [!NOTE]
   > Můžete volně měnit velikost ovládacího prvku <xref:System.Windows.Forms.Panel>, ale nemůžete jeho velikost zmenšit, než je poloha pravého dolního rohu ovládacího prvku <xref:System.Windows.Forms.Button>. Toto chování je určené výchozí hodnotou vlastnosti `AutoSizeMode`, která je <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>.

6. Nastavte hodnotu vlastnosti `AutoSizeMode` ovládacího prvku <xref:System.Windows.Forms.Panel> na <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>.

   Ovládací prvek <xref:System.Windows.Forms.Panel> velikosti sebe sama pro ohraničení ovládacího prvku <xref:System.Windows.Forms.Button>. Nemůžete změnit velikost ovládacího prvku <xref:System.Windows.Forms.Panel>.

7. Přetáhněte ovládací prvek <xref:System.Windows.Forms.Button> směrem k levému hornímu rohu ovládacího prvku <xref:System.Windows.Forms.Panel>.

   Ovládací prvek <xref:System.Windows.Forms.Panel> změní velikost na novou pozici ovládacího prvku <xref:System.Windows.Forms.Button>.

## <a name="next-steps"></a>Další kroky

Pro uspořádání ovládacích prvků v aplikacích model Windows Forms je k dispozici mnoho dalších funkcí rozložení. Tady je několik kombinací, které byste mohli vyzkoušet:

- Sestavte formulář pomocí ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel>. Podrobnosti naleznete v tématu [Návod: uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md). Zkuste změnit hodnoty vlastnosti <xref:System.Windows.Forms.Control.Padding%2A> ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> a také vlastnost <xref:System.Windows.Forms.Control.Margin%2A> u jejích podřízených ovládacích prvků.

- Vyzkoušejte stejný experiment pomocí ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>. Podrobnosti najdete v tématu [Návod: uspořádání ovládacích prvků na model Windows Forms pomocí FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).

- Experimentujte s ukotvením podřízených ovládacích prvků v ovládacím prvku <xref:System.Windows.Forms.Panel>. Vlastnost <xref:System.Windows.Forms.Control.Padding%2A> je obecnější realizace vlastnosti <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> a můžete se ujistit, že se jedná o tento případ tím, že umístíte podřízený ovládací prvek do ovládacího prvku <xref:System.Windows.Forms.Panel> a nastavíte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost podřízeného ovládacího prvku na hodnotu <xref:System.Windows.Forms.DockStyle.Fill>. Nastavte vlastnost <xref:System.Windows.Forms.Control.Padding%2A> ovládacího prvku <xref:System.Windows.Forms.Panel> na různé hodnoty a poznamenejte si účinek.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- [Přehled vlastnosti AutoSize](autosize-property-overview.md)
- [Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Postupy: Uspořádání ovládacích prvků na formuláři Windows Forms s použitím ovládacího prvku FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
