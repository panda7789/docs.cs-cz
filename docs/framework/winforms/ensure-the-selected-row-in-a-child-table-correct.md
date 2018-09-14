---
title: 'Postupy: Zajistěte, aby vybraný řádek v podřízené tabulce zůstal ve správné pozici'
ms.date: 03/30/2017
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
ms.openlocfilehash: e1fdb007451c157e60a1ad723b5d2d06bc85ecdf
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519774"
---
# <a name="how-to-ensure-the-selected-row-in-a-child-table-remains-at-the-correct-position"></a>Postupy: Zajistěte, aby vybraný řádek v podřízené tabulce zůstal ve správné pozici
Často při práci s datovou vazbu v modelu Windows Forms, se zobrazí data v co se nazývá nadřazené a podřízené nebo hlavních/podrobných zobrazení. To se vztahuje na datovou vazbu scénář, kde se zobrazí data ze stejného zdroje ve dvou ovládacích prvků. Změna výběru v jednom ovládacím prvku způsobí, že data zobrazená v druhý ovládací prvek při změně. První ovládací prvek může například obsahovat seznam zákazníků a druhý seznam objednávek týkající se k vybranému zákazníkovi v prvním ovládacím prvku.  
  
 Od verze rozhraní .NET Framework verze 2.0, když se data zobrazí v nadřízené a podřízené zobrazení, že možná budete muset udělat dodatečné kroky, abyste měli jistotu, že není aktuálně vybraný řádek v podřízené tabulce resetování na první řádek tabulky. Pokud to chcete udělat, budete muset podřízená pozice tabulce do mezipaměti a resetujte si ho po změně nadřazené tabulky. Obvykle resetování podřízené dochází poprvé pole za sebou změny nadřazené tabulky.  
  
### <a name="to-cache-the-current-child-position"></a>Pro ukládání do mezipaměti aktuální podřízená pozice  
  
1.  Deklarujte proměnnou celého čísla k uložení umístění seznamu podřízených a logickou hodnotu k ukládání do mezipaměti podřízená pozice.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#4)]  
  
2.  Zpracování <xref:System.Windows.Forms.CurrencyManager.ListChanged> událost pro vazby <xref:System.Windows.Forms.CurrencyManager> a vyhledejte <xref:System.ComponentModel.ListChangedType> z <xref:System.ComponentModel.ListChangedType.Reset>.  
  
3.  Zkontrolujte aktuální pozice <xref:System.Windows.Forms.CurrencyManager>. Pokud je větší než první položka v seznamu (obvykle 0), uložte ji do proměnné.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#2)]  
  
4.  Zpracování nadřazeného seznamu <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> událost pro nadřazený správce měny. V obslužné rutině nastavte logickou hodnotu označující, že se nejedná o scénáři ukládání do mezipaměti. Pokud <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> dojde, změnit na nadřazený prvek je změna pozice seznamu a ne změnit hodnotu položky.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#5)]  
  
### <a name="to-reset-the-child-position"></a>Resetování podřízené pozice  
  
1.  Zpracování <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> událost pro podřízené vazby <xref:System.Windows.Forms.CurrencyManager>.  
  
2.  Resetovat podřízená pozice tabulky na pozici v mezipaměti uloženy v předchozím postupu.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak uložit aktuální pozice <xref:System.Windows.Forms.CurrencyManager>tlačítka podřízenou tabulku a obnovit pozice po dokončení úprav v nadřazené tabulce. Tento příklad obsahuje dva <xref:System.Windows.Forms.DataGridView> ovládací prvky vázané na dvě tabulky v <xref:System.Data.DataSet> pomocí <xref:System.Windows.Forms.BindingSource> komponenty. Navázání vztahu mezi dvěma tabulkami a vztah se přidá do <xref:System.Data.DataSet>. Pozice v podřízené tabulce je zpočátku nastaven na třetí řádek pro demonstrační účely.  
  
 [!code-csharp[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#1)]  
  
 K otestování příklad kódu, proveďte následující kroky:  
  
1.  Spustíte v příkladu.  
  
2.  Ujistěte se, že **mezipaměti a resetování umístit** je zaškrtnuto políčko.  
  
3.  Klikněte na tlačítko **pole vymazat nadřazené** tlačítko a způsobit změnu v poli nadřazené tabulky. Všimněte si, že vybraný řádek v podřízené tabulce nezmění.  
  
4.  Zavřete a znovu spusťte příklad kódu. Musíte to provést, protože se chování obnovení dochází pouze na první změnu v hodnotě nadřazený řádek.  
  
5.  Zrušte **mezipaměti a resetování umístit** zaškrtávací políčko.  
  
6.  Klikněte na tlačítko **pole vymazat nadřazené** tlačítko. Všimněte si, že vybraný řádek v podřízené tabulce se změní na prvním řádku.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Data, System.Drawing, System.Windows.Forms a System.XML.  
  
 Informace o tom, jak sestavovat tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení příkazového řádku s csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Zajištění, aby více ovládacích prvků vázaných ke stejnému zdroji dat zůstalo synchronizovaných](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 [Komponenta BindingSource](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Datové vazby a Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
