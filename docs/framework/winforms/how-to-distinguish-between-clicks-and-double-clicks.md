---
title: 'Postupy: Rozlišení mezi kliknutím a poklikáním'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- mouse [Windows Forms], click
- mouse [Windows Forms], double-click
- mouse clicks [Windows Forms], single versus double
ms.assetid: d836ac8c-85bc-4f3a-a761-8aee03dc682c
ms.openlocfilehash: 84d085700091c4e7b8658e8eac4cf86fbd7730d5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44186276"
---
# <a name="how-to-distinguish-between-clicks-and-double-clicks"></a>Postupy: Rozlišení mezi kliknutím a poklikáním
Obvykle jediného *klikněte na tlačítko* spustí uživatelské rozhraní (UI) akce a *dvakrát klikněte na panel* rozšiřuje akci. Například obvykle vybere položku jedním kliknutím a poklepání upraví vybranou položku. Windows Forms události kliknutí operaci snadno scénář, kde kliknutím a poklepání činnostem nekompatibilní, protože akce spojený s <xref:System.Windows.Forms.Control.Click> nebo <xref:System.Windows.Forms.Control.MouseClick> událostí je provedena akce spojený s <xref:System.Windows.Forms.Control.DoubleClick>nebo <xref:System.Windows.Forms.Control.MouseDoubleClick> událostí. Toto téma ukazuje dvě řešení tohoto problému. Jedním z řešení je zpracování události dvojitým kliknutím a vrátit zpět akce při zpracování událost click. Ve výjimečných případech budete muset simulovat kliknutím a dvakrát klikněte na chování pomocí manipulace <xref:System.Windows.Forms.Control.MouseDown> událostí a s využitím <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> a <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A> vlastnosti <xref:System.Windows.Forms.SystemInformation> třídy. Měří čas mezi klepnutími a pokud druhé kliknutí předchází hodnotu <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> dosažení a kliknutím na se v obdélníku definovaném <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>, dvakrát klikněte na akci provést; v opačném případě klikněte na akci provést.  
  
### <a name="to-roll-back-a-click-action"></a>Chcete-li vrátit zpět akce klikněte na  
  
-   Zkontrolujte, zda má ovládací prvek, že pracujete s standard klikněte dvakrát na chování. Pokud ne, povolte stažení ovládacího prvku s <xref:System.Windows.Forms.Control.SetStyle%2A> metody. Zpracování události dvojitým kliknutím a vrátit zpět akce kliknutí, jakož i dvakrát klikněte na akci. Následující příklad kódu ukazuje vytvoření tlačítka s vlastní s dvojím kliknutím povolené, a také jak vrátit zpět akce kliknutím dvakrát klikněte na událost kód pro zpracování.  
  
     [!code-csharp[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/VB/Form1.vb#1)]  
  
### <a name="to-distinguish-between-clicks-in-the-mousedown-event"></a>K rozlišení mezi kliknutím v MouseDown – událost  
  
-   Zpracování <xref:System.Windows.Forms.Control.MouseDown> události a určit umístění a čas span mezi klepnutími pomocí odpovídající <xref:System.Windows.Forms.SystemInformation> vlastnosti a <xref:System.Windows.Forms.Timer> komponenty. Proveďte příslušné akce v závislosti na tom, jestli kliknutí nebo dvakrát klikněte na něho. Následující příklad kódu ukazuje, jak to lze provést.  
  
     [!code-cpp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/cpp/form1.cpp#0)]
     [!code-csharp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/CS/form1.cs#0)]
     [!code-vb[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tyto příklady vyžadují:  
  
-   Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření těchto příkladech z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tyto příklady v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nové projekty.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 [Vstup z myši v aplikaci Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
