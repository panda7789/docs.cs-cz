---
title: 'Postupy: Zajistěte, aby vybraný řádek v podřízené tabulce zůstal ve správné pozici'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- master-details view
- row position [Windows Forms]
- parent/child view [Windows Forms]
- resetting child position
- data binding [.NET Framework], row selection
- caching [.NET Framework], child position
- child position
- master/details view [Windows Forms]
- child tables row selection
- current child position
ms.assetid: c5fa2562-43a4-46fa-a604-52d8526a87bd
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 30929c6163a279bc0ea47d1262f54ec5ff75a87c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-ensure-the-selected-row-in-a-child-table-remains-at-the-correct-position"></a>Postupy: Zajistěte, aby vybraný řádek v podřízené tabulce zůstal ve správné pozici
Často při práci s datové vazby v systému Windows Forms, se zobrazí data v co se říká nadřazený podřízený nebo hlavní/podrobnosti zobrazení. Vztahuje se k datové vazby scénář, kde se zobrazí data z jednoho zdroje ve dvou ovládacích prvků. Změna výběru v ovládacím prvku jeden způsobí, že data zobrazená v ovládacím prvku druhý změnit. První prvek může například obsahovat seznam zákazníků a druhý seznam objednávek související s vybraného zákazníka v prvním ovládacím.  
  
 Od verze rozhraní .NET Framework verze 2.0, když se data zobrazí v nadřízené a podřízené zobrazení, že možná budete muset udělat dodatečné kroky, abyste měli jistotu, že není aktuálně vybraný řádek v podřízené tabulce resetování na první řádek tabulky. Chcete-li to provést, bude mít ukládat do mezipaměti podřízená pozice tabulky a v něm obnovit po změně nadřazené tabulce. Obvykle resetování podřízené dochází poprvé pole v řádku změn v nadřazené tabulce.  
  
### <a name="to-cache-the-current-child-position"></a>Pro ukládání do mezipaměti aktuální podřízená pozice  
  
1.  Deklarujte celočíselnou proměnnou pro uložení podřízená pozice seznamu a proměnná pro ukládání do mezipaměti podřízená pozice.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#4)]  
  
2.  Zpracování <xref:System.Windows.Forms.CurrencyManager.ListChanged> událost pro vazby <xref:System.Windows.Forms.CurrencyManager> a vyhledejte <xref:System.ComponentModel.ListChangedType> z <xref:System.ComponentModel.ListChangedType.Reset>.  
  
3.  Zkontrolujte aktuální pozici <xref:System.Windows.Forms.CurrencyManager>. Pokud je větší než první položku v seznamu (obvykle 0), uložte ho do proměnné.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#2)]  
  
4.  Zpracování nadřazeného seznamu <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> událost pro správce nadřazené měny. V obslužné rutině nastavte logickou hodnotu označující, že se nejedná o scénáři ukládání do mezipaměti. Pokud <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> dojde, změna s nadřazeným je ke změně pozice v seznamu a není změna hodnoty položky.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#5)]  
  
### <a name="to-reset-the-child-position"></a>Chcete-li obnovit podřízená pozice  
  
1.  Zpracování <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> událost pro podřízený objekt vazby <xref:System.Windows.Forms.CurrencyManager>.  
  
2.  Obnoví podřízená pozice tabulky na pozici v mezipaměti uložena v předchozím postupu.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak uložit na aktuální pozici <xref:System.Windows.Forms.CurrencyManager>.for podřízené tabulce a resetování pozice po dokončení úprav v nadřazené tabulce. Tento příklad obsahuje dva <xref:System.Windows.Forms.DataGridView> ovládací prvky vázané na dvě tabulky <xref:System.Data.DataSet> pomocí <xref:System.Windows.Forms.BindingSource> součásti. Navázání na relaci mezi dvěma tabulkami a vztah se přidá <xref:System.Data.DataSet>. Pozice v podřízené tabulce je zpočátku nastavena na třetí řádek pro demonstrační účely.  
  
 [!code-csharp[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#1)]  
  
 K testování příkladu kódu, proveďte následující kroky:  
  
1.  Spusťte v příkladu.  
  
2.  Zajistěte, aby **mezipaměti a resetování umístit** je zaškrtnuté políčko.  
  
3.  Klikněte **zrušte nadřazeného pole** tlačítko způsobí změnu v poli nadřazené tabulky. Všimněte si, že vybraný řádek v podřízené tabulce se nemění.  
  
4.  Zavřete a znovu spusťte v příkladu. Musíte to provést, protože chování resetování proběhne pouze první změna v nadřazené řádku.  
  
5.  Vymazat **mezipaměti a resetování umístit** zaškrtávací políčko.  
  
6.  Klikněte **zrušte nadřazeného pole** tlačítko. Všimněte si, že vybraný řádek v podřízené tabulce se změní na první řádek.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Data, System.Drawing, System.Windows.Forms a System.XML sestavení.  
  
 Informace o tom, jak vytvořit tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení příkazového řádku s csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Zajištění, aby více ovládacích prvků vázaných ke stejnému zdroji dat zůstalo synchronizovaných](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 [Komponenta BindingSource](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Datové vazby a Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
