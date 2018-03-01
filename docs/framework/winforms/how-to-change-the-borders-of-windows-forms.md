---
title: "Postupy: Změna ohraničení Windows Forms "
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e977617f16ef882ad0dcfe1a96a6e8af73d2ae48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-borders-of-windows-forms"></a>Postupy: Změna ohraničení Windows Forms 
Máte několik stylů ohraničení lze vybírat při určování vzhled a chování Windows Forms. Změnou <xref:System.Windows.Forms.Form.FormBorderStyle%2A> vlastnost, můžete řídit chování změny velikosti ve tvaru. Kromě toho nastavení <xref:System.Windows.Forms.Form.FormBorderStyle%2A> má vliv na způsob zobrazení panelu popisek a co může vypadat tlačítka na něm. Další informace naleznete v tématu <xref:System.Windows.Forms.FormBorderStyle>.  
  
 Je rozsáhlá podpora pro tuto úlohu v [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
 Viz také [postupy: Změna ohraničení Windows Forms pomocí návrháře](http://msdn.microsoft.com/library/yettzh3e\(v=vs.110\)).  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a>Chcete-li nastavit styl ohraničení Windows Forms prostřednictvím kódu programu  
  
-   Nastavte <xref:System.Windows.Forms.Form.FormBorderStyle%2A> vlastnost na styl chcete. Následující příklad kódu nastaví styl ohraničení tvaru `DlgBx1` k <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     Viz také [postupy: vytvoření dialogová okna v době návrhu](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\)).  
  
     Kromě toho pokud jste vybrali styl ohraničení pro daný formulář, který poskytuje volitelné **minimalizaci** a **Maximalizovat** tlačítka, které můžete určete, jestli má jedné nebo obou těchto tlačítek k fungování. Tyto přepínače jsou užitečné, když chcete řídí činnost koncového uživatele. **Minimalizaci** a **Maximalizovat** tlačítka jsou povolena ve výchozím nastavení, a jejich funkce s nimi manipulovat prostřednictvím **vlastnosti** okno.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.FormBorderStyle>  
 <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>  
 [Začínáme s Windows Forms](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
