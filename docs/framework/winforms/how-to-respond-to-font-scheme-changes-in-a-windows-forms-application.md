---
title: "Postupy: Odpověď na změny schématu písem ve formulářové aplikaci Windows"
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
helpviewer_keywords: Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aac8d56c87ff03b313565a3d04cd3f3cc4e85f72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a>Postupy: Odpověď na změny schématu písem ve formulářové aplikaci Windows
V operačních systémech Windows uživatel může změnit nastavení systémového písma, aby byly výchozí písmo zobrazí větší nebo menší. Změna těchto nastavení písma je velmi důležitá pro uživatele, kteří jsou slabozraké a vyžadují větší typ ke čtení textu na obrazovce. Můžete upravit aplikaci Windows Forms reagování na tyto změny zvýšením nebo snížením velikosti formulář a všechny obsažené text vždy, když změny schématu písem. Pokud chcete, aby svého formuláře dynamicky zohlednit změny velikosti písem, můžete přidat kód do svého formuláře.  
  
 Výchozí písmo použité ve Windows Forms je obvykle písmo vrácený <xref:Microsoft.Win32> volání obor názvů `GetStockObject(DEFAULT_GUI_FONT)`. Písmo vrácený toto volání se změní jenom v případě změny rozlišení obrazovky. Jak je znázorněno v následujícím postupu, kódu musíte změnit výchozí písmo na <xref:System.Drawing.SystemFonts.IconTitleFont%2A> reagovat na změny velikosti písma.  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a>Použít plochy písma a reagovat na změny schématu písem  
  
1.  Vytvořte svého formuláře a ovládací prvky, které chcete přidat do ní. Další informace najdete v tématu [postupy: Vytvoření Formulářové aplikace Windows z příkazového řádku](../../../docs/framework/winforms/how-to-create-a-windows-forms-application-from-the-command-line.md) a [ovládací prvky používané ve formulářích Windows](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).  
  
2.  Přidat odkaz na <xref:Microsoft.Win32> oboru názvů do vašeho kódu.  
  
     [!code-csharp[WinFormsAutoScaling#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3.  Přidejte následující kód do konstruktoru objektu svého formuláře spojit Obslužné rutiny požadované událostí a chcete-li změnit písmo výchozí používá pro daný formulář.  
  
     [!code-csharp[WinFormsAutoScaling#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4.  Implementujte obslužnou rutinu pro <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> událost, která způsobí, že formulář automaticky škálovat při <xref:Microsoft.Win32.UserPreferenceCategory.Window> kategorie změny.  
  
     [!code-csharp[WinFormsAutoScaling#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5.  Nakonec implementovat obslužnou rutinu pro <xref:System.Windows.Forms.Form.FormClosing> událost, která umožňuje odpojit <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> obslužné rutiny události.  
  
> [!IMPORTANT]
>  Selhání zahrnout tento kód způsobí, že vaše aplikace a nastat únik paměti.  
  
 [!code-csharp[WinFormsAutoScaling#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
 [!code-vb[WinFormsAutoScaling#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
1.  Zkompilování a spuštění kódu.  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a>Ruční změny schématu písem v systému Windows XP  
  
1.  Když je spuštěna aplikace Windows Forms, klikněte pravým tlačítkem na ploše systému Windows a vyberte **vlastnosti** z místní nabídky.  
  
2.  V **vlastností zobrazení** dialogové okno, klikněte na tlačítko **vzhled** kartě.  
  
3.  Z **velikost písma** rozevíracího seznamu vyberte novou velikost písma.  
  
     Si všimnete, že formulář nyní reaguje na spuštění čas změny ve schématu plochy písma. Když uživatel změní mezi **normální**, **velká písma**, a **navíc velká písma**, formulář změní písmo a škáluje správně.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[WinFormsAutoScaling#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 Constructer v tomto příkladu kódu obsahuje volání `InitializeComponent`, který je definován při vytvoření nového projektu Windows Forms v sadě Visual Studio. Pokud vytváříte aplikace na příkazovém řádku, odeberte tento řádek kódu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>  
 [Automatická změna měřítka ve Windows Forms](../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md)
