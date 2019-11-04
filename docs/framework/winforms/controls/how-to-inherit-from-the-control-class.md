---
title: 'Postupy: Dědění ze třídy Control'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7af7d1fe8f14c71dfc90836d84023b98feb44961
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458380"
---
# <a name="how-to-inherit-from-the-control-class"></a>Postupy: Dědění ze třídy Control

Chcete-li vytvořit zcela vlastní ovládací prvek pro použití ve formuláři Windows, měli byste dědit z třídy <xref:System.Windows.Forms.Control>. Při dědění z třídy <xref:System.Windows.Forms.Control> vyžaduje, abyste provedli další plánování a implementaci, ale také poskytujete největší rozsah možností. Při dědění z <xref:System.Windows.Forms.Control>zdědíte velmi základní funkce, které ovládací prvky usnadňují práci. Funkce, které jsou součástí třídy <xref:System.Windows.Forms.Control>, zpracovává vstup uživatele prostřednictvím klávesnice a myši, definuje meze a velikost ovládacího prvku, nabízí popisovač systému Windows a poskytuje řízení a zabezpečení zpráv. Nezahrnuje žádné vykreslování, což je v tomto případě skutečné vykreslování grafického rozhraní ovládacího prvku, ani nezahrnuje žádné konkrétní funkce interakce s uživatelem. Všechny tyto aspekty je nutné poskytnout prostřednictvím vlastního kódu.

## <a name="to-create-a-custom-control"></a>Vytvoření vlastního ovládacího prvku

1. V aplikaci Visual Studio vytvořte novou **aplikaci systému Windows** nebo projekt **knihovny ovládacích prvků systému** Windows.

2. V nabídce **projekt** vyberte možnost **Přidat třídu**.

3. V dialogovém okně **Přidat novou položku** klikněte na **vlastní ovládací prvek**.

   Do projektu se přidá nový vlastní ovládací prvek.

4. Stisknutím klávesy **F7** otevřete **Editor kódu** vlastního ovládacího prvku.

5. Vyhledejte metodu <xref:System.Windows.Forms.Control.OnPaint%2A>, která bude prázdná s výjimkou volání metody <xref:System.Windows.Forms.Control.OnPaint%2A> základní třídy.

6. Upravte kód tak, aby zahrnoval jakékoli vlastní vykreslení, které chcete pro svůj ovládací prvek.

   Informace o psaní kódu pro vykreslení grafiky ovládacích prvků naleznete v tématu [vlastní ovládací prvky Malování a vykreslování](custom-control-painting-and-rendering.md).

7. Implementujte jakékoli vlastní metody, vlastnosti nebo události, které bude váš ovládací prvek obsahovat.

8. Uložte a otestujte svůj ovládací prvek.

## <a name="see-also"></a>Viz také:

- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
- [Postupy: Dědění ze třídy UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Postupy: Dědění ze stávajících ovládacích prvků Windows Forms](how-to-inherit-from-existing-windows-forms-controls.md)
- [Postupy: Vytváření ovládacích prvků pro Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Řešení potíží se zděděnými obslužnými rutinami událostí v Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Vývoj ovládacích prvků Windows Forms v době návrhu](developing-windows-forms-controls-at-design-time.md)
