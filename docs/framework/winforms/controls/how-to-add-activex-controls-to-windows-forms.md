---
title: 'Postupy: Přidávání ovládacích prvků ActiveX do formulářů Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 68e25cb2cd7e1f1c63954b20d24f028a49431553
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707986"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>Postupy: Přidávání ovládacích prvků ActiveX do formulářů Windows
Zatímco Návrhář formulářů Windows je optimalizována pro hostitelské ovládací prvky Windows Forms, lze také umístit ovládací prvky ActiveX v modelu Windows Forms.  
  
> [!CAUTION]
>  Existují omezení výkonu pro Windows Forms, kdy ovládací prvky ActiveX jsou k nim přidány.  
  
 Předtím, než přidáte do svého formuláře ovládací prvky ActiveX, musíte je přidat do panelu nástrojů. Další informace najdete v tématu [komponenty modelu COM, dialogové okno přizpůsobení panelu nástrojů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, klikněte na tlačítko **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a>Chcete-li přidat ovládací prvek ActiveX do formuláře Windows  
  
-   Poklepejte na ovládací prvek na panelu nástrojů.  
  
     Visual Studio přidá všechny odkazy na ovládací prvek ve vašem projektu. Další informace o co je potřeba vzít v úvahu při použití ovládacích prvků ActiveX do formulářů Windows, naleznete v tématu [aspekty hostování ovládacího prvku ActiveX ve formuláři Windows](considerations-when-hosting-an-activex-control-on-a-windows-form.md).  
  
    > [!NOTE]
    >  Importér ovládacích prvků ActiveX Windows Forms (AxImp.exe) vytvoří argumenty událostí jiného typu než se čekalo na Import knihoven DLL ActiveX. Argumenty vytvořené AxImp.exe se nějak takto: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, když `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` se očekává. Mějte na paměti, že tato nesrovnalost nebrání kód funguje normálně. Podrobnosti najdete v tématu [Importér ovládacích prvků Windows Forms ActiveX (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).  
  
## <a name="see-also"></a>Viz také:
- [Windows Forms – ovládací prvky](index.md)
- [Ovládacích prvků a programovatelných objektů porovnáno v různých jazycích a knihovnách](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [Postupy: Přidání ovládacích prvků do formulářů Windows](how-to-add-controls-to-windows-forms.md)
- [Uspořádávání ovládacích prvků ve Windows Forms](arranging-controls-on-windows-forms.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Ovládací prvky Windows Forms podle funkce](windows-forms-controls-by-function.md)
