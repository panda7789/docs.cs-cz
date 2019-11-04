---
title: 'Postupy: Dědění ze třídy UserControl'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 10bb807d012a130ad633b7ce06f99c5abf2cdda1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458368"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a>Postupy: Dědění ze třídy UserControl

Chcete-li kombinovat funkce jednoho nebo více model Windows Forms ovládacích prvků s vlastním kódem, můžete vytvořit *uživatelský ovládací prvek*. Uživatelské ovládací prvky kombinují rychlý vývoj ovládacích prvků, standardní funkce řízení model Windows Forms a univerzálnost vlastních vlastností a metod. Po zahájení vytváření uživatelského ovládacího prvku se zobrazí viditelný Návrhář, na kterém můžete umístit standardní model Windows Forms ovládací prvky. Tyto ovládací prvky zachovávají veškerou svou vlastní funkčnost a také vzhled a chování (vzhled a chování) standardních ovládacích prvků. Jakmile jsou tyto ovládací prvky integrovány do uživatelského ovládacího prvku, nejsou již k dispozici prostřednictvím kódu. Uživatelský ovládací prvek provádí vlastní Malování a také zpracovává všechny základní funkce přidružené k ovládacím prvkům.

## <a name="to-create-a-user-control"></a>Vytvoření uživatelského ovládacího prvku

1. Vytvořte nový projekt **knihovny ovládacích prvků systému Windows** v aplikaci Visual Studio.

   Vytvoří se nový projekt s prázdným uživatelským ovládacím prvkem.

2. Přetáhněte ovládací prvky z karty **model Windows Forms** **panelu nástrojů** do návrháře.

3. Tyto ovládací prvky by měly být umístěny a navrženy tak, jak se mají zobrazovat v konečném uživatelském ovládacím prvku. Chcete-li vývojářům dovolit přístup k ovládacím prvkům prvku, je nutné je deklarovat jako veřejné nebo selektivně vystavit vlastnosti ovládacího prvku prvku. Podrobnosti naleznete v tématu [How to: vystavování vlastností ovládacích prvků](how-to-expose-properties-of-constituent-controls.md)prvku.

4. Implementujte všechny vlastní metody nebo vlastnosti, které bude váš ovládací prvek obsahovat.

5. Stisknutím klávesy **F5** Sestavte projekt a spusťte ovládací prvek v **kontejneru testu UserControl**. Další informace naleznete v tématu [How to: test runtime Behavior prvku UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).

## <a name="see-also"></a>Viz také:

- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
- [Postupy: Dědění ze třídy Control](how-to-inherit-from-the-control-class.md)
- [Postupy: Dědění ze stávajících ovládacích prvků Windows Forms](how-to-inherit-from-existing-windows-forms-controls.md)
- [Postupy: Vytváření ovládacích prvků pro Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Řešení potíží se zděděnými obslužnými rutinami událostí v Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Postupy: Otestování běhového chování UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
