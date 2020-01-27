---
title: Reakce na změny schématu písem v aplikaci model Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: e3b96139a7cfd4b268d81b1da58229527e2beb87
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739225"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a>Postupy: Odpověď na změny schématu písem v aplikaci Windows Forms
V operačních systémech Windows může uživatel změnit nastavení písem v rámci systému tak, aby výchozí písmo bylo větší nebo menší. Změna těchto nastavení písma je zásadní pro uživatele, kteří jsou vizuálně poškozeni a vyžadují větší typ pro čtení textu na svých obrazovkách. Aplikaci model Windows Forms můžete upravit tak, aby reagovala na tyto změny tím, že se zvětší nebo zmenší velikost formuláře a veškerý text, kdykoli se změní schéma písem. Pokud chcete, aby formulář přizpůsobil změny velikosti písma dynamicky, můžete do formuláře přidat kód.  
  
 Výchozí písmo, které používá model Windows Forms, je obvykle písmo, které je vráceno voláním <xref:Microsoft.Win32> oboru názvů do `GetStockObject(DEFAULT_GUI_FONT)`. Písmo vrácené tímto voláním se změní pouze při změně rozlišení obrazovky. Jak je znázorněno v následujícím postupu, váš kód musí změnit výchozí písmo, aby <xref:System.Drawing.SystemFonts.IconTitleFont%2A> reagovat na změny velikosti písma.  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a>Použití písma desktopu a reakce na změny schématu písem  
  
1. Vytvořte formulář a přidejte do něj ovládací prvky, které chcete do něj přidat. Další informace najdete v tématu [Postup: Vytvoření aplikace model Windows Forms z příkazového řádku](how-to-create-a-windows-forms-application-from-the-command-line.md) a [ovládací prvky pro použití v model Windows Forms](./controls/controls-to-use-on-windows-forms.md).  
  
2. Přidejte odkaz na obor názvů <xref:Microsoft.Win32> do kódu.  
  
     [!code-csharp[WinFormsAutoScaling#2](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3. Přidejte následující kód do konstruktoru formuláře pro zapojení požadovaných obslužných rutin událostí a pro změnu výchozího písma používaného pro formulář.  
  
     [!code-csharp[WinFormsAutoScaling#3](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4. Implementujte obslužnou rutinu pro událost <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>, která způsobuje automatické škálování formuláře při změně kategorie <xref:Microsoft.Win32.UserPreferenceCategory.Window>.  
  
     [!code-csharp[WinFormsAutoScaling#4](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5. Nakonec Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.Form.FormClosing>, která odpojí obslužnou rutinu události <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.  
  
     > [!IMPORTANT]
     > Pokud nechcete tento kód zahrnout do paměti, může vaše aplikace nevrácená paměť.  
  
     [!code-csharp[WinFormsAutoScaling#5](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6. Zkompilujte a spusťte kód.  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a>Ruční změna schématu písem v systému Windows XP  
  
1. Když je vaše aplikace model Windows Forms spuštěná, klikněte pravým tlačítkem myši na plochu Windows a v místní nabídce vyberte **vlastnosti** .  
  
2. V dialogovém okně **zobrazení vlastností** klikněte na kartu **vzhled** .  
  
3. V rozevíracím seznamu **Velikost písma** vyberte novou velikost písma.  
  
     Všimněte si, že formulář nyní reaguje na změny za běhu ve schématu písem pro stolní počítače. Když se uživatel změní mezi **normálním**, **velkým písmem**a **dalšími velkými**písmy, změní formulář písmo a správně škáluje.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[WinFormsAutoScaling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 Konstruktor v tomto příkladu kódu obsahuje volání `InitializeComponent`, které je definováno při vytváření nového projektu model Windows Forms v aplikaci Visual Studio. Odeberte tento řádek kódu, pokud vytváříte aplikaci na příkazovém řádku.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- [Automatická změna měřítka ve Windows Forms](automatic-scaling-in-windows-forms.md)
