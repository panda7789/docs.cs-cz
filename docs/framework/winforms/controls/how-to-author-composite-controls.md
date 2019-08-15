---
title: 'Postupy: Vytváření složených ovládacích prvků'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
ms.openlocfilehash: 7b0ee8efa62175e2ced2a810ca6dd76e8adc103b
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039885"
---
# <a name="how-to-author-composite-controls"></a>Postupy: Vytváření složených ovládacích prvků

Složené ovládací prvky mohou být zaměstnány mnoha způsoby. Můžete je vytvořit jako součást projektu desktopové aplikace systému Windows a použít ji pouze pro formuláře v projektu. Nebo je můžete vytvořit v projektu knihovny ovládacích prvků systému Windows, zkompilovat projekt do sestavení a použít ovládací prvky v jiných projektech. Z nich můžete dokonce dědit a použít dědění vizuálu k jejich rychlému přizpůsobení pro zvláštní účely.

> [!NOTE]
> Chcete-li vytvořit složený ovládací prvek pro použití ve webových formulářích, přečtěte si téma [vývoj vlastních ovládacích prvků ASP.NET serveru](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).

## <a name="to-author-a-composite-control"></a>Vytváření složeného ovládacího prvku

1. V aplikaci Visual Studio vytvořte nový projekt **aplikace systému Windows** s `DemoControlHost`názvem.

2. V nabídce **projekt** klikněte na příkaz **Přidat uživatelský ovládací prvek**.

3. V dialogovém okně **Přidat novou položku** poskytněte souboru třídy (soubor. vb nebo. cs) název, který má složený ovládací prvek mít.

4. Vyberte tlačítko **Přidat** , chcete-li vytvořit soubor třídy pro složený ovládací prvek.

5. Přidejte ovládací prvky ze **sady nástrojů** do složené plochy ovládacího prvku.

6. Umístěte kód do procedur událostí pro zpracování událostí vyvolaných složeným ovládacím prvkem nebo ovládacími prvky prvku.

7. Zavřete návrháře složeného ovládacího prvku a uložte soubor po zobrazení výzvy.

8. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

     Aby se v **sadě nástrojů**zobrazovaly vlastní ovládací prvky, musí být projekt sestaven.

9. Použijte kartu **DemoControlHost** sady **nástrojů** k přidání instancí ovládacího prvku do `Form1`.

## <a name="to-author-a-control-class-library"></a>Chcete-li vytvořit knihovnu tříd ovládacích prvků

1. Otevřete nový projekt **knihovny ovládacích prvků systému Windows** .

     Ve výchozím nastavení projekt obsahuje složený ovládací prvek.

2. Přidejte ovládací prvky a kód, jak je popsáno výše v postupu.

3. Vyberte ovládací prvek, který nechcete dědit třídy, a nastavte vlastnost modifikátory tohoto ovládacího prvku na hodnotu **Private**.

4. Sestavení knihovny DLL.

## <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a>Dědění ze složeného ovládacího prvku v knihovně tříd ovládacích prvků

1. V nabídce **soubor** přejděte na příkaz **Přidat** a vyberte **Nový projekt** a přidejte do řešení nový projekt **aplikace pro Windows** .

2. V **Průzkumník řešení**klikněte pravým tlačítkem myši na složku **odkazy** pro nový projekt a vyberte možnost **Přidat odkaz** . tím otevřete dialogové okno **Přidat odkaz** .

3. Vyberte kartu **projekty** a dvakrát klikněte na projekt knihovny ovládacích prvků.

4. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

5. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt knihovny ovládacích prvků a v místní nabídce vyberte možnost **Přidat novou položku** .

6. Vyberte šablonu **zděděného uživatelského ovládacího prvku** z dialogového okna **Přidat novou položku** .

7. V dialogovém okně **Výběr dědičnosti** dvakrát klikněte na ovládací prvek, ze kterého chcete dědit.

     Do projektu se přidá nový ovládací prvek.

8. Otevřete vizuálního návrháře pro nový ovládací prvek a přidejte další ovládací prvky prvku.

     Můžete vidět ovládací prvky prvku, které byly zděděny ze složeného ovládacího prvku v knihovně DLL, a můžete změnit vlastnosti ovládacích prvků, jejichž Modifikátory vlastnost je **Veřejná**. Nemůžete změnit vlastnosti ovládacího prvku, jehož vlastnost modifikátory je **soukromá**.

## <a name="see-also"></a>Viz také:

- [Návod: Vytváření složeného ovládacího prvku pomocí Visual Basic](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [Návod: Vytváření složeného ovládacího prvku pomocí vizuáluC#](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [Návod: Dědění z ovládacího prvku model Windows Forms s Visual Basic](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [Návod: Dědění z ovládacího prvku model Windows Forms pomocí vizuáluC#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
- [Doporučení ohledně typu ovládacího prvku](control-type-recommendations.md)
- [Postupy: Vytváření ovládacích prvků pro model Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
