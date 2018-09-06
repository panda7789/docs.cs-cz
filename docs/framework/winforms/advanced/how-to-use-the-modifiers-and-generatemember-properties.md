---
title: 'Postupy: Používání modifikátorů a vlastností GenerateMember'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- Designer_GenerateMember
- Designer_Modifiers
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 3381a5e4-e1a3-44e2-a765-a0b758937b85
ms.openlocfilehash: 9bb6e6568822f3edcabf50a4fceb7cc6386f05ef
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43869205"
---
# <a name="how-to-use-the-modifiers-and-generatemember-properties"></a>Postupy: Používání modifikátorů a vlastností GenerateMember
Umístíte-li komponenta ve formuláři Windows Forms, podle návrhu prostředí jsou k dispozici dvě vlastnosti: `GenerateMember` a `Modifiers`. `GenerateMember` Vlastnost určuje, když Návrhář formulářů Windows generuje členské proměnné pro komponentu. `Modifiers` Vlastnost je modifikátor přístupu, které jsou přiřazeny k této členské proměnné. Pokud hodnota `GenerateMember` vlastnost `false`, hodnota `Modifiers` vlastnost nemá žádný vliv.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-specify-whether-a-component-is-a-member-of-the-form"></a>Chcete-li určit, zda je součást člena ve tvaru  
  
1.  V Návrháři formulářů Windows otevřete formulář.  
  
2.  Otevřít **nástrojů**a ve formuláři, umístěte tři <xref:System.Windows.Forms.Button> ovládacích prvků.  
  
3.  Nastavte `GenerateMember` a `Modifiers` vlastnosti pro každý <xref:System.Windows.Forms.Button> ovládací prvek podle následující tabulky.  
  
    |Název tlačítka|Generatemember – hodnota|Modifikátory hodnota|  
    |-----------------|--------------------------|---------------------|  
    |`button1`|`true`|`private`|  
    |`button2`|`true`|`protected`|  
    |`button3`|`false`|Žádné změny|  
  
4.  Sestavte řešení.  
  
5.  V **Průzkumníka řešení**, klikněte na tlačítko **zobrazit všechny soubory** tlačítko.  
  
6.  Otevřete **Form1** uzel a **Editor kódu**, otevřete **Form1.Designer.vb** nebo **Form1.Designer.cs** souboru. Tento soubor obsahuje kód, protože ho vygeneroval Návrhář formulářů Windows.  
  
7.  Najdete deklarace pro tři tlačítka. Následující příklad kódu ukazuje rozdíly určené `GenerateMember` a `Modifiers` vlastnosti.  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]  
  
> [!NOTE]
>  Ve výchozím nastavení, Návrhář formulářů Windows přiřadí `private` (`Friend` v jazyce Visual Basic) modifikátor pro ovládací prvky kontejneru jako <xref:System.Windows.Forms.Panel>. Pokud základním <xref:System.Windows.Forms.UserControl> nebo <xref:System.Windows.Forms.Form> má ovládací prvek kontejneru, nebude přijímat nové podřízené položky v zděděný ovládací prvky a formuláře. Řešením je změnit modifikátor základní kontejneru ovládacího prvku na `protected` nebo `public`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Button>  
 [Vizuální dědění modelu Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [Návod: Demonstrace vizuálního dědění](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)  
 [Postupy: Dědění v modelu Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)
