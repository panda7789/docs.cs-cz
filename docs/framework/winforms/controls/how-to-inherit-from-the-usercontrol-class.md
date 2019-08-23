---
title: 'Postupy: Dědění ze třídy UserControl'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
ms.openlocfilehash: 77233517203989f188a2b3ddf436656bc8da82a6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966569"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a>Postupy: Dědění ze třídy UserControl
Chcete-li kombinovat funkce jednoho nebo více model Windows Forms ovládacích prvků s vlastním kódem, můžete vytvořit *uživatelský ovládací prvek*. Uživatelské ovládací prvky kombinují rychlý vývoj ovládacích prvků, standardní funkce řízení model Windows Forms a univerzálnost vlastních vlastností a metod. Po zahájení vytváření uživatelského ovládacího prvku se zobrazí viditelný Návrhář, na kterém můžete umístit standardní model Windows Forms ovládací prvky. Tyto ovládací prvky zachovávají veškerou svou vlastní funkčnost a také vzhled a chování (vzhled a chování) standardních ovládacích prvků. Jakmile jsou tyto ovládací prvky integrovány do uživatelského ovládacího prvku, nejsou již k dispozici prostřednictvím kódu. Uživatelský ovládací prvek provádí vlastní Malování a také zpracovává všechny základní funkce přidružené k ovládacím prvkům.

## <a name="to-create-a-user-control"></a>Vytvoření uživatelského ovládacího prvku

1. Vytvořte nový projekt **knihovny ovládacích prvků systému Windows** .

     Vytvoří se nový projekt s prázdným uživatelským ovládacím prvkem.

2. Přetáhněte ovládací prvky z karty **model Windows Forms** **panelu nástrojů** do návrháře.

3. Tyto ovládací prvky by měly být umístěny a navrženy tak, jak se mají zobrazovat v konečném uživatelském ovládacím prvku. Chcete-li vývojářům dovolit přístup k ovládacím prvkům prvku, je nutné je deklarovat jako veřejné nebo selektivně vystavit vlastnosti ovládacího prvku prvku. Podrobnosti najdete v tématu [How to: Zveřejňuje vlastnosti ovládacích prvků](how-to-expose-properties-of-constituent-controls.md)prvku.

4. Implementujte všechny vlastní metody nebo vlastnosti, které bude váš ovládací prvek obsahovat.

5. Stisknutím klávesy F5 Sestavte projekt a spusťte ovládací prvek v **kontejneru testu UserControl**. Další informace najdete v tématu [jak: Otestuje chování prvku UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)v době běhu.

## <a name="see-also"></a>Viz také:

- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
- [Postupy: Zdědit z třídy ovládacího prvku](how-to-inherit-from-the-control-class.md)
- [Postupy: Zdědit z existujících ovládacích prvků model Windows Forms](how-to-inherit-from-existing-windows-forms-controls.md)
- [Postupy: Vytváření ovládacích prvků pro model Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Řešení potíží se zděděnými obslužnými rutinami událostí v Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Postupy: Testování chování prvku UserControl v době běhu](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
