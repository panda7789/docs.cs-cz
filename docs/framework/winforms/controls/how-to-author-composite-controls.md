---
title: 'Postupy: Vytváření složených ovládacích prvků'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 42ea424507b89576df8099fd4849dd2665135a55
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459435"
---
# <a name="how-to-author-composite-controls"></a>Postupy: vytváření složených ovládacích prvků

Složené ovládací prvky mohou být zaměstnány mnoha způsoby. Můžete je vytvořit jako součást projektu desktopové aplikace systému Windows a použít ji pouze pro formuláře v projektu. Nebo je můžete vytvořit v projektu knihovny ovládacích prvků systému Windows, zkompilovat projekt do sestavení a použít ovládací prvky v jiných projektech. Z nich můžete dokonce dědit a použít dědění vizuálu k jejich rychlému přizpůsobení pro zvláštní účely.

## <a name="to-author-a-composite-control"></a>Vytváření složeného ovládacího prvku

1. V aplikaci Visual Studio vytvořte nový projekt **aplikace pro Windows** a pojmenujte ho **DemoControlHost**.

2. V nabídce **projekt** klikněte na příkaz **Přidat uživatelský ovládací prvek**.

3. V dialogovém okně **Přidat novou položku** poskytněte souboru třídy (soubor. vb nebo. cs) název, který má složený ovládací prvek mít.

4. Vyberte tlačítko **Přidat** , chcete-li vytvořit soubor třídy pro složený ovládací prvek.

5. Přidejte ovládací prvky ze **sady nástrojů** do složené plochy ovládacího prvku.

6. Umístěte kód do procedur událostí pro zpracování událostí vyvolaných složeným ovládacím prvkem nebo ovládacími prvky prvku.

7. Zavřete návrháře složeného ovládacího prvku a uložte soubor po zobrazení výzvy.

8. V nabídce **sestavení** klikněte na **Sestavit řešení**.

     Aby se v **sadě nástrojů**zobrazovaly vlastní ovládací prvky, musí být projekt sestaven.

9. Pomocí karty **DemoControlHost** sady **nástrojů** přidejte instance ovládacího prvku do `Form1`.

## <a name="to-author-a-control-class-library"></a>Chcete-li vytvořit knihovnu tříd ovládacích prvků

1. Otevřete nový projekt **knihovny ovládacích prvků systému Windows** .

     Ve výchozím nastavení projekt obsahuje složený ovládací prvek.

2. Přidejte ovládací prvky a kód, jak je popsáno výše v postupu.

3. Vyberte ovládací prvek, který nechcete dědit třídy, a nastavte vlastnost **modifikátory** tohoto ovládacího prvku na hodnotu **Private**.

4. Sestavení knihovny DLL.

## <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a>Dědění ze složeného ovládacího prvku v knihovně tříd ovládacích prvků

1. V nabídce **soubor** přejděte na příkaz **Přidat** a vyberte **Nový projekt** a přidejte do řešení nový projekt **aplikace pro Windows** .

2. V **Průzkumník řešení**klikněte pravým tlačítkem myši na složku **odkazy** pro nový projekt a vyberte možnost **Přidat odkaz** . tím otevřete dialogové okno **Přidat odkaz** .

3. Vyberte kartu **projekty** a dvakrát klikněte na projekt knihovny ovládacích prvků.

4. V nabídce **sestavení** klikněte na **Sestavit řešení**.

5. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt knihovny ovládacích prvků a v místní nabídce vyberte možnost **Přidat novou položku** .

6. Vyberte šablonu **zděděného uživatelského ovládacího prvku** z dialogového okna **Přidat novou položku** .

7. V dialogovém okně **Výběr dědičnosti** dvakrát klikněte na ovládací prvek, ze kterého chcete dědit.

     Do projektu se přidá nový ovládací prvek.

8. Otevřete vizuálního návrháře pro nový ovládací prvek a přidejte další ovládací prvky prvku.

     Můžete vidět ovládací prvky prvku, které byly zděděny ze složeného ovládacího prvku v knihovně DLL, a můžete změnit vlastnosti ovládacích prvků, jejichž **modifikátory** vlastnost je **Veřejná**. Nemůžete změnit vlastnosti ovládacího prvku, jehož vlastnost **modifikátory** je **soukromá**.

## <a name="see-also"></a>Viz také:

- [Návod: vytváření složeného ovládacího prvku](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [Návod: dědění z ovládacího prvku model Windows Forms](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
- [Doporučení ohledně typu ovládacího prvku](control-type-recommendations.md)
- [Postupy: Vytváření ovládacích prvků pro Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
