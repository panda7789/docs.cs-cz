---
title: 'Postupy: Odpověď na změny schématu písem v aplikaci Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: 85770687ecfad690a251eafec9051c4c20f45dd2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182101"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a>Postupy: Odpověď na změny schématu písem v aplikaci Windows Forms
V operačních systémech Windows uživatel může změnit nastavení systémová písma a ujistěte se zobrazí výchozí písmo větší nebo menší. Změna těchto písmo nastavení je velmi důležité pro uživatele, kteří jsou slabozraké a vyžadují větší typ čtení textu na obrazovce. Můžete upravit aplikaci Windows Forms k reagovat na tyto změny zvýšením nebo snížením velikosti formuláře a veškerý text při každé změně schématu písem. Pokud chcete formuláře dynamicky přizpůsobí změny velikosti písma, můžete přidat kód do formuláře.  
  
 Obvykle je výchozí písmo použité ve Windows Forms písma vrácené <xref:Microsoft.Win32> obor názvů volání `GetStockObject(DEFAULT_GUI_FONT)`. Pokud se rozlišení změní pouze změní písmo vrácený toto volání. Jak je znázorněno v následujícím postupu, musí váš kód změnit výchozí písmo na <xref:System.Drawing.SystemFonts.IconTitleFont%2A> reakce na změny velikosti písma.  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a>Písmo plochy pomocí a reagovat na změny schématu písem  
  
1.  Vytvoření formuláře a ovládací prvky, které chcete přidat do ní. Další informace najdete v tématu [jak: Vytvoření aplikace Windows Forms z příkazového řádku](how-to-create-a-windows-forms-application-from-the-command-line.md) a [ovládací prvky používané ve formulářích Windows](./controls/controls-to-use-on-windows-forms.md).  
  
2.  Přidejte odkaz na <xref:Microsoft.Win32> oboru názvů do vašeho kódu.  
  
     [!code-csharp[WinFormsAutoScaling#2](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3.  Přidejte následující kód do konstruktoru formuláře k obslužné rutiny události požadované připojení a chcete-li změnit výchozí písmo používané pro daný formulář.  
  
     [!code-csharp[WinFormsAutoScaling#3](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4.  Implementujte obslužnou rutinu pro <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> událost, která způsobí, že formulář pro automatické škálování při <xref:Microsoft.Win32.UserPreferenceCategory.Window> změny kategorií.  
  
     [!code-csharp[WinFormsAutoScaling#4](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5.  A konečně, implementujte obslužnou rutinu pro <xref:System.Windows.Forms.Form.FormClosing> událost, která se odpojí <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> obslužné rutiny události.  
  
     > [!IMPORTANT]
     > Nepodařilo se přidat tento kód způsobí aplikace únik paměti.  
  
     [!code-csharp[WinFormsAutoScaling#5](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6.  Kompilace a spuštění kódu.  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a>Ruční změny schématu písem ve Windows XP  
  
1.  Když je spuštěna aplikace Windows Forms, klikněte pravým tlačítkem na plochu Windows a zvolte **vlastnosti** z místní nabídky.  
  
2.  V **vlastnosti zobrazení** dialogové okno, klikněte na tlačítko **vzhled** kartu.  
  
3.  Z **velikost písma** rozevíracího seznamu vyberte novou velikost písma.  
  
     Můžete si všimnout, že formulář nyní reaguje na změny za běhu v režimu plochy písma. Když uživatel změní mezi **normální**, **velká písma**, a **další velký písma**, formulář se změní písmo a škáluje správně.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[WinFormsAutoScaling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 Constructer v tomto příkladu kód obsahuje volání `InitializeComponent`, který je definován při vytváření nového projektu Windows Forms v sadě Visual Studio. Odeberte tento řádek kódu, pokud vytváříte aplikaci na příkazovém řádku.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- [Automatická změna měřítka ve Windows Forms](automatic-scaling-in-windows-forms.md)
