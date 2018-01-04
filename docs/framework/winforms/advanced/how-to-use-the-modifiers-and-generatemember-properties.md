---
title: "Postupy: Používání modifikátorů a vlastností GenerateMember"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f524bab55527bf9d3c744cb6f50d1df1fc9a2302
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-modifiers-and-generatemember-properties"></a>Postupy: Používání modifikátorů a vlastností GenerateMember
Když umístíte komponentu ve formuláři Windows, dvě vlastnosti jsou k dispozici v prostředí návrhu: `GenerateMember` a `Modifiers`. `GenerateMember` Vlastnost určuje, kdy Návrhář formulářů Windows generuje členské proměnné pro součást. `Modifiers` Vlastnost je – modifikátor přístupu, které jsou přiřazeny k této proměnné členů. Pokud hodnota `GenerateMember` vlastnost je `false`, hodnota `Modifiers` vlastnost nemá žádný efekt.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-specify-whether-a-component-is-a-member-of-the-form"></a>K určení, zda je součást členem formuláře  
  
1.  V Návrháři formulářů Windows otevřete formulář.  
  
2.  Otevřete **sada nástrojů**a na formuláři, umístěte tři <xref:System.Windows.Forms.Button> ovládací prvky.  
  
3.  Nastavte `GenerateMember` a `Modifiers` vlastnosti pro každou <xref:System.Windows.Forms.Button> řízení podle následující tabulky.  
  
    |Název tlačítka|Generatemember – hodnota|Modifikátory hodnota|  
    |-----------------|--------------------------|---------------------|  
    |`button1`|`true`|`private`|  
    |`button2`|`true`|`protected`|  
    |`button3`|`false`|Žádná změna|  
  
4.  Sestavte řešení.  
  
5.  V **Průzkumníku řešení**, klikněte **zobrazit všechny soubory** tlačítko.  
  
6.  Otevřete **Form1** uzel a v **Editor kódu**, otevřete **Form1.Designer.vb** nebo **Form1.Designer.cs** souboru. Tento soubor obsahuje kód vysílaných Návrhář formulářů Windows.  
  
7.  Najít deklarace pro tři tlačítka. Následující příklad kódu ukazuje rozdíly určeného `GenerateMember` a `Modifiers` vlastnosti.  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]  
  
> [!NOTE]
>  Ve výchozím nastavení, Návrhář formulářů Windows přiřadí `private` (`Friend` v jazyce Visual Basic) modifikátor pro ovládací prvky kontejneru jako <xref:System.Windows.Forms.Panel>. Pokud vaše základní <xref:System.Windows.Forms.UserControl> nebo <xref:System.Windows.Forms.Form> má ovládacího prvku kontejner nebude přijímat nové podřízených prvků ve formulářích a zděděné ovládací prvky. Řešení je změna modifikátor základní kontejneru ovládacího prvku na `protected` nebo `public`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Button>  
 [Vizuální dědění modelu Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [Návod: Demonstrace vizuálního dědění](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)  
 [Postupy: Dědění v modelu Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)
