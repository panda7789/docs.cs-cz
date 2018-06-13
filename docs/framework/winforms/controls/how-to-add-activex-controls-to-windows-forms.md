---
title: 'Postupy: Přidávání ovládacích prvků ActiveX do formulářů Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: c851a215638e60642bf93564f4884b5a79d430d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527375"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>Postupy: Přidávání ovládacích prvků ActiveX do formulářů Windows
Zatímco Návrhář formulářů Windows je optimalizovaná tak, aby hostitelské ovládací prvky Windows Forms, můžete taky v rozhraní Windows Forms – ovládací prvky ActiveX.  
  
> [!CAUTION]
>  Existují omezení výkonu pro Windows Forms, když jsou do nich přidány ovládací prvky ActiveX.  
  
 Než přidáte do svého formuláře ovládací prvky ActiveX, musíte je přidat do sady nástrojů. Další informace najdete v tématu [komponenty modelu COM, dialogové okno přizpůsobení sady nástrojů](http://msdn.microsoft.com/library/171333f3-f207-4e02-bbdc-17862556212c).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, klikněte na tlačítko **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a>Přidání ovládacího prvku ActiveX do svého formuláře Windows  
  
-   Dvakrát klikněte na ovládací prvek v panelu nástrojů.  
  
     Visual Studio přidá všechny odkazy na ovládací prvek v projektu. Další informace o aspektech, které při použití na Windows Forms – ovládací prvky ActiveX mějte na paměti najdete v tématu [aspekty hostování ovládacího prvku ActiveX ve formuláři Windows](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md).  
  
    > [!NOTE]
    >  Systému Windows Forms ActiveX – Importér ovládacích prvků (AxImp.exe) vytvoří argumenty událostí jiného typu než se čekalo na Import ActiveX dynamické knihovny. Argumenty vytvořené AxImp.exe jsou podobné následujícím: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, když `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` se očekává. Upozorňujeme, že tato nesrovnalost nezabrání kód fungovat normálně. Podrobnosti najdete v tématu [Windows Forms ActiveX – Importér ovládacích prvků (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md).  
  
## <a name="see-also"></a>Viz také  
 [Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/index.md)  
 [Ovládací prvky a programovatelný objekty porovnání v různých jazycích a knihovny](http://msdn.microsoft.com/library/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [Postupy: Přidávání ovládacích prvků do Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [Uspořádávání ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Ovládací prvky Windows Forms podle funkce](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
