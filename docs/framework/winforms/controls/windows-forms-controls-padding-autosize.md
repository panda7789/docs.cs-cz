---
title: 'Návod: Rozvrhování ovládacích prvků Windows Forms s odsazením, okraji a s vlastností AutoSize'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: daf0c6495b89033e75c27a1ff0cbceaff9d85f34
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987166"
---
# <a name="walkthrough-lay-out-controls-with-padding-margins-and-the-autosize-property"></a>Návod: Rozvrhnout ovládací prvky s odsazením, okraji a vlastností AutoSize

Přesné umístění ovládacích prvků ve formuláři je velmi prioritní pro mnoho aplikací. **Návrhář formulářů** v aplikaci Visual Studio poskytuje mnoho nástrojů pro rozložení, které by to bylo možné provést. Tři z nejdůležitějších jsou <xref:System.Windows.Forms.Control.Margin%2A>vlastnosti, <xref:System.Windows.Forms.Control.Padding%2A>a <xref:System.Windows.Forms.Control.AutoSize%2A> , které jsou k dispozici u všech model Windows Formsch ovládacích prvků.

<xref:System.Windows.Forms.Control.Margin%2A> Vlastnost definuje prostor kolem ovládacího prvku, který uchovává jiné ovládací prvky o určenou vzdálenost od ohraničení ovládacího prvku.

Vlastnost definuje prostor uvnitř ovládacího prvku, který udržuje obsah ovládacího prvku (například hodnota jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnosti) o zadanou vzdálenost od ohraničení ovládacího prvku. <xref:System.Windows.Forms.Control.Padding%2A>

Následující ilustrace znázorňuje <xref:System.Windows.Forms.Control.Padding%2A> vlastnosti a <xref:System.Windows.Forms.Control.Margin%2A> na ovládacím prvku.

![Odsazení a okraj pro ovládací prvky model Windows Forms](./media/vs-winformpadmargin.gif)

<xref:System.Windows.Forms.Control.AutoSize%2A> Vlastnost oznamuje ovládacímu prvku automatickou velikost obsahu. Velikost se nemění tak, aby byla menší než hodnota jeho původní <xref:System.Windows.Forms.Control.Size%2A> vlastnosti, a bude se považovat za hodnotu jeho <xref:System.Windows.Forms.Control.Padding%2A> vlastnosti.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto Názorného postupu budete potřebovat Visual Studio.

## <a name="create-the-project"></a>Vytvoření projektu

1. V aplikaci Visual Studio vytvořte projekt **aplikace systému Windows** s `LayoutExample`názvem.

2. Vyberte formulář v **Návrhář formulářů**.

## <a name="set-margins-for-controls"></a>Nastavit okraje pro ovládací prvky

Výchozí vzdálenost mezi ovládacími prvky můžete nastavit pomocí <xref:System.Windows.Forms.Control.Margin%2A> vlastnosti. Když přesunete ovládací prvek dostatečně blízko k jinému ovládacímu prvku, zobrazí se snapline, který zobrazuje okraje pro tyto dva ovládací prvky. Ovládací prvek, který přesouváte, bude také přichycený ke vzdálenosti definované okraji.

### <a name="arrange-controls-on-your-form-using-the-margin-property"></a>Uspořádání ovládacích prvků na formuláři pomocí vlastnosti okraj

1. Přetáhněte dva <xref:System.Windows.Forms.Button> ovládací prvky ze **sady nástrojů** do formuláře.

2. Vyberte jeden z <xref:System.Windows.Forms.Button> ovládacích prvků a přesuňte ho blízko k druhému, dokud nebudou skoro dotek.

   Sledujte snapline, která se mezi nimi nacházejí. Tato vzdálenost je součtem <xref:System.Windows.Forms.Control.Margin%2A> hodnot dvou ovládacích prvků. Ovládací prvek, na který se přesouváte, se přitahuje na tuto vzdálenost. Podrobnosti najdete v tématu [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)zarovnávacím čárám.

3. <xref:System.Windows.Forms.Padding.All%2A> <xref:System.Windows.Forms.Control.Margin%2A>Změňte vlastnost jednoho z ovládacích prvků rozšířením položky v okně Vlastnosti a nastavením vlastnosti na hodnotu 20. <xref:System.Windows.Forms.Control.Margin%2A>

4. Vyberte jeden z <xref:System.Windows.Forms.Button> ovládacích prvků a přesuňte ho blízko k druhému.

   SnapLine definující součet hodnot okrajů je delší a ovládací prvek se přitahuje na větší vzdálenost od druhého ovládacího prvku.

5. <xref:System.Windows.Forms.Padding.Top%2A> <xref:System.Windows.Forms.Control.Margin%2A>Změňte vlastnost vybraného ovládacího prvku rozbalením položky v okně Vlastnosti a nastavením vlastnosti na hodnotu 5. <xref:System.Windows.Forms.Control.Margin%2A>

6. Přesuňte vybraný ovládací prvek pod druhým ovládacím prvkem a sledujte, zda je snapline kratší. Přesuňte vybraný ovládací prvek nalevo od druhého ovládacího prvku a sledujte, že snapline zachovává hodnotu zjištěnou v kroku 4.

7. <xref:System.Windows.Forms.Control.Margin%2A> Můžete nastavit všechny aspekty vlastnosti, <xref:System.Windows.Forms.Padding.Left%2A>, <xref:System.Windows.Forms.Padding.Top%2A> <xref:System.Windows.Forms.Padding.Right%2A> <xref:System.Windows.Forms.Padding.All%2A> ,,, na jiné hodnoty nebo je můžete nastavit na stejnou hodnotu s vlastností. <xref:System.Windows.Forms.Padding.Bottom%2A>

## <a name="set-padding-for-controls"></a>Nastavit odsazení pro ovládací prvky

Chcete-li dosáhnout přesného rozložení požadovaného pro aplikaci, ovládací prvky budou často obsahovat podřízené ovládací prvky. Pokud chcete určit blízkost okraje podřízeného ovládacího prvku na ohraničení nadřazeného ovládacího prvku, použijte <xref:System.Windows.Forms.Control.Padding%2A> vlastnost nadřazeného ovládacího prvku ve spojení s <xref:System.Windows.Forms.Control.Margin%2A> vlastností podřízeného ovládacího prvku. Vlastnost slouží také k řízení blízkosti obsahu ovládacího prvku (například <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Text%2A> vlastnosti ovládacího prvku) k jeho ohraničení. <xref:System.Windows.Forms.Control.Padding%2A>

### <a name="arrange-controls-on-your-form-using-padding"></a>Uspořádání ovládacích prvků na formuláři pomocí odsazení

1. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.Button>

2. Změňte hodnotu <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnosti ovládacího prvku na **hodnotu true**.

3. <xref:System.Windows.Forms.Padding.All%2A>Změňte vlastnost rozbalením položky v okně Vlastnosti a nastavením vlastnosti na hodnotu 5. <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.Control.Padding%2A>

   Ovládací prvek se rozšíří a poskytne prostor pro nové odsazení.

4. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.GroupBox> Přetáhněte ovládací prvek ze <xref:System.Windows.Forms.GroupBox> **sady nástrojů** do ovládacího prvku. <xref:System.Windows.Forms.Button> Umístěte ovládací prvek tak, aby byl vyprázdněn v pravém dolním rohu <xref:System.Windows.Forms.GroupBox> ovládacího prvku. <xref:System.Windows.Forms.Button>

   Sledujte zarovnávacím čárám, který se zobrazí jako <xref:System.Windows.Forms.Button> ovládací prvek, se blíží dolnímu a pravému okraji <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Tyto zarovnávacím čárám odpovídají <xref:System.Windows.Forms.Control.Margin%2A> vlastnosti <xref:System.Windows.Forms.Button>.

5. <xref:System.Windows.Forms.Control.Padding%2A> Rozbalením<xref:System.Windows.Forms.Control.Padding%2A>položkyv okně **vlastnosti** a nastavením <xref:System.Windows.Forms.GroupBox>vlastnosti na hodnotu 20 změňte vlastnost ovládacího prvku. <xref:System.Windows.Forms.Padding.All%2A>

6. Vyberte ovládací prvek <xref:System.Windows.Forms.GroupBox> v ovládacím prvku a přesuňte ho <xref:System.Windows.Forms.GroupBox>směrem ke středu. <xref:System.Windows.Forms.Button>

   Zarovnávacím čárám se zobrazí ve větší vzdálenosti od ohraničení <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Tato vzdálenost je součtem <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Margin%2A> vlastnostiovládacího<xref:System.Windows.Forms.GroupBox> prvku a vlastnostiovládacíhoprvku.<xref:System.Windows.Forms.Control.Padding%2A>

## <a name="size-controls-automatically"></a>Nastavit velikost ovládacích prvků automaticky

V některých aplikacích nebude velikost ovládacího prvku stejná v době běhu, protože byla v době návrhu. Text <xref:System.Windows.Forms.Button> ovládacího prvku může být například z databáze převeden a jeho délka není známa předem.

`true`Pokud je <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost nastavena na, změní se ovládací prvek na jeho obsah. Další informace naleznete v tématu [Přehled vlastností AutoSize](autosize-property-overview.md).

### <a name="arrange-controls-on-your-form-using-the-autosize-property"></a>Uspořádání ovládacích prvků ve formuláři pomocí vlastnosti AutoSize

1. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.Button>

2. Změňte hodnotu <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnosti ovládacího prvku na **hodnotu true**.

3. <xref:System.Windows.Forms.Button> Změňte vlastnost<xref:System.Windows.Forms.Control.Text%2A> ovládacího prvku na **Toto tlačítko má dlouhý řetězec pro jeho vlastnost text**.

   Když změnu potvrdíte, <xref:System.Windows.Forms.Button> ovládací prvek změní velikost sebe sama tak, aby odpovídala novému textu.

4. Přetáhněte jiný <xref:System.Windows.Forms.Button> ovládací prvek z **panelu nástrojů** do formuláře.

5. <xref:System.Windows.Forms.Button> Změňte vlastnost<xref:System.Windows.Forms.Control.Text%2A> ovládacího prvku na "**Toto tlačítko má dlouhý řetězec pro jeho vlastnost text".**

   Při potvrzení změny <xref:System.Windows.Forms.Button> se ovládací prvek sám nemění a text bude oříznutý pravým okrajem ovládacího prvku.

6. <xref:System.Windows.Forms.Padding.All%2A>Změňte vlastnost rozbalením položky v okně Vlastnosti a nastavením vlastnosti na hodnotu 5. <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.Control.Padding%2A>

   Text v vnitřku ovládacího prvku se ořízne na všech čtyřech stranách.

7. <xref:System.Windows.Forms.Button> Změňte vlastnost<xref:System.Windows.Forms.Control.AutoSize%2A> ovládacího prvku na **hodnotu true**.

   <xref:System.Windows.Forms.Button> Ovládací prvek změní velikost sebe sama tak, aby zahrnovala celý řetězec. Kolem textu bylo přidáno také odsazení, což způsobí, že se <xref:System.Windows.Forms.Button> ovládací prvek rozbalí do všech čtyř směrů.

8. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.Button> Umístěte ho poblíž pravého dolního rohu formuláře.

9. Změňte hodnotu <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnosti ovládacího prvku na **hodnotu true**.

10. <xref:System.Windows.Forms.Button> Nastavte vlastnost<xref:System.Windows.Forms.Control.Anchor%2A> ovládacího prvku na <xref:System.Windows.Forms.AnchorStyles.Right>,. <xref:System.Windows.Forms.AnchorStyles.Bottom>

11. <xref:System.Windows.Forms.Button> Změňte vlastnost<xref:System.Windows.Forms.Control.Text%2A> ovládacího prvku na "**Toto tlačítko má dlouhý řetězec pro jeho vlastnost text".**

   Když změnu potvrdíte, <xref:System.Windows.Forms.Button> ovládací prvek změní velikost směrem doleva. Obecně platí, že Automatická změna velikosti zvýší velikost ovládacího prvku v opačném směru jako jeho <xref:System.Windows.Forms.Control.Anchor%2A> nastavení vlastnosti.

## <a name="autosize-and-autosizemode-properties"></a>Vlastnosti AutoSize a AutoSizeMode

 Některé ovládací prvky podporují `AutoSizeMode` vlastnost, která poskytuje přesnější kontrolu nad chováním ovládacího prvku při automatické změně velikosti.

### <a name="use-the-autosizemode-property"></a>Použití vlastnosti AutoSizeMode

1. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.Panel>

2. Nastavte hodnotu <xref:System.Windows.Forms.Panel> <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnosti ovládacího prvku na **hodnotu true**.

3. Přetáhněte ovládací prvek ze <xref:System.Windows.Forms.Panel> **sady nástrojů** do ovládacího prvku. <xref:System.Windows.Forms.Button>

4. Umístěte ovládací prvek poblíž pravého dolního rohu <xref:System.Windows.Forms.Panel> ovládacího prvku. <xref:System.Windows.Forms.Button>

5. <xref:System.Windows.Forms.Panel> Vyberte ovládací prvek a napravte u něj dolní úchyt pro změnu velikosti. Změňte velikost <xref:System.Windows.Forms.Panel> ovládacího prvku tak, aby byl větší a menší.

   > [!NOTE]
   > Můžete změnit <xref:System.Windows.Forms.Panel> velikost ovládacího prvku, ale nemůžete jeho velikost zmenšit, než je poloha <xref:System.Windows.Forms.Button> pravého dolního rohu ovládacího prvku. Toto chování je určeno výchozí hodnotou `AutoSizeMode` vlastnosti, což je. <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>

6. Nastavte hodnotu <xref:System.Windows.Forms.Panel> `AutoSizeMode` vlastnosti ovládacího prvku na <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>.

   Ovládací prvek omezuje velikost <xref:System.Windows.Forms.Button> ovládacího prvku tak, aby obklopuje ovládací prvek. <xref:System.Windows.Forms.Panel> Nemůžete změnit <xref:System.Windows.Forms.Panel> velikost ovládacího prvku.

7. Přetáhněte ovládací prvek směrem k levému hornímu rohu <xref:System.Windows.Forms.Panel> ovládacího prvku. <xref:System.Windows.Forms.Button>

   Ovládací prvek se změní <xref:System.Windows.Forms.Button> na novou pozici ovládacího prvku. <xref:System.Windows.Forms.Panel>

## <a name="next-steps"></a>Další postup

Pro uspořádání ovládacích prvků v aplikacích model Windows Forms je k dispozici mnoho dalších funkcí rozložení. Tady je několik kombinací, které byste mohli vyzkoušet:

- Sestavte formulář pomocí <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku. Podrobnosti najdete v tématu [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)TableLayoutPanel. Zkuste změnit hodnoty <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.Control.Padding%2A> vlastnosti ovládacího prvku <xref:System.Windows.Forms.Control.Margin%2A> , stejně jako vlastnost u jejích podřízených ovládacích prvků.

- Vyzkoušejte stejný experiment pomocí <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Podrobnosti najdete v tématu [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).

- Experimentujte s ukotvením podřízených ovládacích <xref:System.Windows.Forms.Panel> prvků v ovládacím prvku. Vlastnost je obecnější realizace <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> vlastnosti a můžete se ujistit, že se jedná o tento případ tím, že umístíte podřízený ovládací prvek do <xref:System.Windows.Forms.Panel> ovládacího prvku a nastavíte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost podřízeného ovládacího prvku na <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Panel> Nastavte vlastnost<xref:System.Windows.Forms.Control.Padding%2A> ovládacího prvku na různé hodnoty a poznamenejte si účinek.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- [Přehled vlastnosti AutoSize](autosize-property-overview.md)
- [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí zarovnávacím čárám](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
