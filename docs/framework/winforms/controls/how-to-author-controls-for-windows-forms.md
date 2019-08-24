---
title: 'Postupy: Vytváření ovládacích prvků pro Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 45a6ae68102204ad8506027065c2676e02fdd7a3
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015921"
---
# <a name="how-to-author-controls-for-windows-forms"></a>Postupy: Vytváření ovládacích prvků pro model Windows Forms

Ovládací prvek představuje grafické propojení mezi uživatelem a programem. Ovládací prvek může poskytovat nebo zpracovávat data, přijímat vstup uživatele, reagovat na události nebo provádět libovolný počet dalších funkcí, které spojují uživatele a aplikaci. Vzhledem k tomu, že ovládací prvek je v podstatě komponenta s grafickým rozhraním, může obsluhovat jakoukoli funkci, kterou komponenta dělá, a poskytnout interakci s uživatelem. Ovládací prvky jsou vytvořeny pro poskytování konkrétních účelů a ovládací prvky pro vytváření obsahu jsou pouze další úlohy programování. V takovém případě následující kroky reprezentují přehled procesu vytváření ovládacích prvků. Odkazy poskytují další informace o jednotlivých krocích.

## <a name="to-author-a-control"></a>Chcete-li vytvořit ovládací prvek

1. Určete, jak chcete, aby váš ovládací prvek vyzkoušel nebo co jeho součást bude možné ve vaší aplikaci přehrát. Faktory, které je potřeba vzít v úvahu:

    - Jaký druh grafického rozhraní potřebujete?

    - Jakou interakci s uživatelem tento ovládací prvek zpracuje?

    - Je funkce, kterou potřebujete k dispozici u všech stávajících ovládacích prvků?

    - Funkce, které potřebujete, můžete získat kombinováním několika model Windows Formsch ovládacích prvků?

2. Pokud potřebujete objektový model pro ovládací prvek, určete, jak budou distribuovány funkce v celém objektovém modelu a rozdělte funkce mezi ovládací prvek a všechny podobjekty. Objektový model může být užitečný, pokud plánujete složitý ovládací prvek nebo chcete začlenit několik funkcí.

3. Určete typ ovládacího prvku (například uživatelský ovládací prvek, vlastní ovládací prvek, zděděný model Windows Forms ovládací prvek), který potřebujete. Podrobnosti naleznete v tématu [doporučení typu ovládacího prvku](control-type-recommendations.md) a [odrůdy vlastních ovládacích prvků](varieties-of-custom-controls.md).

4. Rychlé funkce jako vlastnosti, metody a události ovládacího prvku a jeho podřízených objektů nebo poboček a přiřadí příslušné úrovně přístupu (například Public, Protected atd.).

5. Pokud pro svůj ovládací prvek potřebujete vlastní malování, přidejte pro něj kód. Podrobnosti najdete v tématu [Malování a vykreslování vlastního ovládacího prvku](custom-control-painting-and-rendering.md).

6. Pokud váš ovládací prvek dědí <xref:System.Windows.Forms.UserControl>z, můžete otestovat jeho chování za běhu sestavením projektu ovládacího prvku a jeho spuštěním v **kontejneru testu UserControl**. Další informace najdete v tématu [jak: Otestuje chování prvku UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)v době běhu.

7. Můžete také otestovat a ladit ovládací prvek vytvořením nového projektu, jako je například aplikace systému Windows, a umístěním do kontejneru. Tento proces je znázorněný v rámci [návodu: Vytváření složeného ovládacího](walkthrough-authoring-a-composite-control-with-visual-csharp.md)prvku.

8. Když přidáte jednotlivé funkce, přidejte do projektu testů funkce pro uplatnění nových funkcí.

9. Opakujte návrh návrhu.

10. Zabalení a nasazení ovládacího prvku Podrobnosti najdete v tématu [první pohled na nasazení v aplikaci Visual Studio](/visualstudio/deployment/deploying-applications-services-and-components).

## <a name="see-also"></a>Viz také:

- [Postupy: Zdědit z třídy UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Postupy: Zdědit z třídy ovládacího prvku](how-to-inherit-from-the-control-class.md)
- [Postupy: Zdědit z existujících ovládacích prvků model Windows Forms](how-to-inherit-from-existing-windows-forms-controls.md)
- [Postupy: Testování chování prvku UserControl v době běhu](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
