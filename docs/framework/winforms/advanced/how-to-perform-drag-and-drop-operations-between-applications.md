---
title: 'Postupy: Provádění operací přetažení myší mezi aplikacemi'
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms], between applications
ms.assetid: fa347436-2b12-4dd6-8507-59d7241f6a06
ms.openlocfilehash: 1e9556a69f3f5da4a47c5f5b1a6043a9a73dd8ff
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713433"
---
# <a name="how-to-perform-drag-and-drop-operations-between-applications"></a>Postupy: Provádění operací přetažení myší mezi aplikacemi
Provádění operací přetažení myší mezi aplikacemi se nijak neliší od povolení této akce v rámci aplikace, tak dlouho, dokud zahrnuté obě aplikace chovat podle "smlouva" mezi <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> a <xref:System.Windows.Forms.DragEventArgs.Effect%2A> Vlastnosti.  
  
 V následujícím postupu budete používat aplikace založené na Windows, které vytvoříte a WordPad textový procesor, který je součástí operačního systému Windows k provádění operací přetažení myší mezi aplikacemi. WordPad má určitou sadu povolené efekty text, který je přetáhnout; aplikace založené na Windows, které budete psát kód pro spolupráci s negativních dopadů tak, aby se může úspěšně dokončit operace přetažení myší.  
  
### <a name="to-perform-a-drag-and-drop-procedure-between-applications"></a>Postup a přetažení mezi aplikacemi  
  
1.  Vytvoření nové aplikace Windows Forms.  
  
2.  Přidat <xref:System.Windows.Forms.TextBox> ovládací prvek do formuláře.  
  
3.  Konfigurace <xref:System.Windows.Forms.TextBox> ovládací prvek přijímat vynechaných data.  
  
     Další informace najdete v tématu [názorný postup: Operace a přetažení ve Windows Forms](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).  
  
4.  Spuštění aplikace založené na Windows a když je spuštěná aplikace, spustit program WordPad.  
  
     WordPad je textový editor a nainstalované ve Windows, který umožňuje operace přetažení myší. Stisknutím kombinace kláves je přístupný **Start** tlačítka, výběr **spustit**a zadáním `WordPad` do textového pole **spustit** dialogové okno a kliknutím na **OK**.  
  
5.  Jakmile WordPad otevře, zadejte do něj textového řetězce.  
  
6.  Pomocí myši, vyberte text a pak přetáhněte vybraný text na <xref:System.Windows.Forms.TextBox> ovládacího prvku v aplikaci založené na Windows.  
  
     Pozorujte, že když najedete myší <xref:System.Windows.Forms.TextBox> ovládacího prvku (a v důsledku toho vyvolat <xref:System.Windows.Forms.Control.DragEnter> událostí), změní se kurzor který lze přetáhnout vybraný text do <xref:System.Windows.Forms.TextBox> ovládacího prvku.  
  
     Kromě toho můžete nakonfigurovat váš <xref:System.Windows.Forms.TextBox> ovládací prvek umožňující textových řetězců, které se přetáhnout do WordPad. Další informace najdete v tématu [názorný postup: Operace a přetažení ve Windows Forms](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Přidání dat do schránky.](how-to-add-data-to-the-clipboard.md)
- [Postupy: Načtení dat ze schránky](how-to-retrieve-data-from-the-clipboard.md)
- [Operace přetažení a podpora schránky](drag-and-drop-operations-and-clipboard-support.md)
