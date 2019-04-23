---
title: 'Postupy: Uzamykání ovládacích prvků ve Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: ac5fbf33564ed2dd1a030132a35b36164f777519
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59301695"
---
# <a name="how-to-lock-controls-to-windows-forms"></a>Postupy: Uzamykání ovládacích prvků ve Windows Forms
Při návrhu uživatelského rozhraní (UI) aplikace Windows můžete uzamknout ovládací prvky, jakmile náleží správně, tak, aby nikoli neúmyslně přesunout nebo změnit jejich velikost, při nastavení dalších vlastností.  
  
 Kromě toho můžete zamknutí a odemknutí všech ovládacích prvků na formuláři najednou, který je užitečný pro formuláře s mnoho ovládacích prvků, nebo můžete odemknout jednotlivých ovládacích prvků. Jakmile všechny ovládací prvky mají umístit kamkoli chcete ve formuláři, uzamknout je vše na místo, kde můžete zabránit přesunu chybné.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-lock-a-control"></a>Uzamknout ovládací prvek  
  
1. V **vlastnosti** okna, klikněte na tlačítko **uzamčené** vlastnosti a vyberte `true`. (Poklepete na název přepíná nastavení vlastnosti.)  
  
     Alternativně klikněte pravým tlačítkem na ovládací prvek a vyberte **uzamknout ovládací prvky**.  
  
    > [!NOTE]
    >  Uzamykání ovládacích prvků jim to brání přetažen novou velikost nebo umístění na návrhové ploše. Ale můžete pořád změnit velikost nebo umístění ovládacích prvků prostřednictvím **vlastnosti** okna nebo v kódu.  
  
### <a name="to-lock-all-the-controls-on-a-form"></a>Uzamknout ovládací prvky ve formuláři  
  
1. Z **formátu** nabídce zvolte **uzamknout ovládací prvky**.  
  
    > [!NOTE]
    >  Tento příkaz uzamkne velikost formuláře, protože formulář je ovládací prvek.  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a>K odemknutí všechny uzamčené ovládací prvky ve formuláři  
  
1. Z **formátu** nabídce zvolte **uzamknout ovládací prvky**.  
  
     Všechny předtím zamčenými ovládací prvky ve formuláři jsou teď odemknout.  
  
### <a name="to-unlock-locked-controls-individually"></a>Odemknout uzamčení jednotlivě ovládacích prvků  
  
1. V **vlastnosti** okna, klikněte na tlačítko **uzamčené** vlastnosti a vyberte `false`. (Poklepete na název přepíná nastavení vlastnosti.)  
  
## <a name="see-also"></a>Viz také:

- [Windows Forms – ovládací prvky](index.md)
- [Uspořádávání ovládacích prvků ve Windows Forms](arranging-controls-on-windows-forms.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Ovládací prvky Windows Forms podle funkce](windows-forms-controls-by-function.md)
