---
title: 'Postupy: Vytváření nadřazených formulářů MDI'
description: Naučte se vytvořit nadřazený formulář MDI programově a pomocí Návrhář formulářů.
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
ms.openlocfilehash: d387837a565ca247f62828c19f353990b35117c7
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174702"
---
# <a name="how-to-create-mdi-parent-forms"></a>Postupy: Vytváření nadřazených formulářů MDI

> [!IMPORTANT]
> Toto téma používá <xref:System.Windows.Forms.MainMenu> ovládací prvek, který byl nahrazen <xref:System.Windows.Forms.MenuStrip> ovládacím prvkem. <xref:System.Windows.Forms.MainMenu>Ovládací prvek se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. Informace o vytvoření nadřazeného formuláře MDI pomocí a <xref:System.Windows.Forms.MenuStrip> naleznete v tématu [How to: Create a Window MDI list with MenuStrip](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).

Základem aplikace MDI (Multiple Document Interface) je nadřazený formulář MDI. Jedná se o formulář, který obsahuje podřízená okna MDI, což je dílčí systém Windows, podle kterého uživatel pracuje s aplikací MDI. Vytvoření nadřazeného formuláře MDI je jednoduché v Návrhář formulářů i programově.

## <a name="create-an-mdi-parent-form-at-design-time"></a>Vytvoření nadřazeného formuláře MDI v době návrhu

1. Vytvořte projekt aplikace pro Windows v aplikaci Visual Studio.

2. V okně **vlastnosti** nastavte <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost na **hodnotu true**.

     Tato položka označuje formulář jako kontejner MDI pro podřízená okna.

    > [!NOTE]
    > Při nastavování vlastností v okně **vlastnosti** můžete také nastavit `WindowState` vlastnost na **maximalizovat**, pokud chcete, protože je nejjednodušší pracovat s podřízenými okny MDI při maximalizaci nadřazeného formuláře. Kromě toho mějte na paměti, že hrana nadřazeného formuláře MDI vybere systémovou barvu (nastavenou v ovládacím panelu systém Windows) místo barvy pozadí, kterou jste nastavili pomocí <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> Vlastnosti.

3. Z **panelu nástrojů**přetáhněte ovládací prvek **MenuStrip** do formuláře. Vytvořte položku nabídky nejvyšší úrovně s vlastností **text** nastavenou na **&soubor** s položkami podnabídky s názvem **&New** a **&Close**. Vytvořte také položku nabídky nejvyšší úrovně s názvem **&okno**.

     První nabídka vytvoří a skryje položky nabídky za běhu a druhá nabídka bude sledovat otevřené podřízené okna MDI. V tomto okamžiku jste vytvořili nadřazené okno MDI.

4. Stisknutím klávesy **F5** spusťte aplikaci. Informace o vytváření podřízených oken MDI, které pracují v nadřazeném formuláři MDI, naleznete v tématu [How to: Create MDI-podřízené formuláře](how-to-create-mdi-child-forms.md).

## <a name="see-also"></a>Viz také

- [Aplikace MDI (Multiple-Document Interface)](multiple-document-interface-mdi-applications.md)
- [Postupy: Vytváření podřízených formulářů MDI](how-to-create-mdi-child-forms.md)
- [Postupy: Určení podřízeného prvku aktivního MDI](how-to-determine-the-active-mdi-child.md)
- [Postupy: Odesílání dat do aktivního podřízeného MDI](how-to-send-data-to-the-active-mdi-child.md)
- [Postupy: Uspořádání podřízených formulářů MDI](how-to-arrange-mdi-child-forms.md)
