---
title: Nastavení odsazení, předsazení a odstavců s odrážkami pomocí ovládacího prvku RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], setting indents
- .rtf files [Windows Forms], formatting in RichTextBox control
- examples [Windows Forms], text boxes
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting indents and bullets
- text boxes [Windows Forms], bullets
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
ms.openlocfilehash: 4dcd5691f328eac6d94675c50ed41a7d7cc36596
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743015"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="4ebf0-102">Postupy: Nastavení odsazení, ukotvených odsazení a odstavců s odrážkami pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="4ebf0-102">How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="4ebf0-103">Ovládací prvek model Windows Forms <xref:System.Windows.Forms.RichTextBox> má mnoho možností formátování textu, který zobrazuje.</span><span class="sxs-lookup"><span data-stu-id="4ebf0-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="4ebf0-104">Vybrané odstavce můžete formátovat jako seznamy s odrážkami nastavením vlastnosti <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>.</span><span class="sxs-lookup"><span data-stu-id="4ebf0-104">You can format selected paragraphs as bulleted lists by setting the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property.</span></span> <span data-ttu-id="4ebf0-105">Pomocí vlastností <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>a <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> můžete také nastavit odsazení odstavců vzhledem k levému a pravému okraji ovládacího prvku a levý okraj dalších řádků textu.</span><span class="sxs-lookup"><span data-stu-id="4ebf0-105">You can also use the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, and <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> properties to set the indentation of paragraphs relative to the left and right edges of the control, and the left edge of other lines of text.</span></span>  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a><span data-ttu-id="4ebf0-106">Formátování odstavce jako seznamu s odrážkami</span><span class="sxs-lookup"><span data-stu-id="4ebf0-106">To format a paragraph as a bulleted list</span></span>  
  
1. <span data-ttu-id="4ebf0-107">Vlastnost <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> nastavte na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="4ebf0-107">Set the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property to `true`.</span></span>  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### <a name="to-indent-a-paragraph"></a><span data-ttu-id="4ebf0-108">Odsazení odstavce</span><span class="sxs-lookup"><span data-stu-id="4ebf0-108">To indent a paragraph</span></span>  
  
1. <span data-ttu-id="4ebf0-109">Nastavte vlastnost <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> na celé číslo představující vzdálenost v pixelech mezi levým okrajem ovládacího prvku a levým okrajem textu.</span><span class="sxs-lookup"><span data-stu-id="4ebf0-109">Set the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> property to an integer representing the distance in pixels between the left edge of the control and the left edge of the text.</span></span>  
  
2. <span data-ttu-id="4ebf0-110">Nastavte vlastnost <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> na celé číslo představující vzdálenost v pixelech mezi levým okrajem prvního řádku textu v odstavci a levým okrajem dalších řádků ve stejném odstavci.</span><span class="sxs-lookup"><span data-stu-id="4ebf0-110">Set the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property to an integer representing the distance in pixels between the left edge of the first line of text in the paragraph and the left edge of subsequent lines in the same paragraph.</span></span> <span data-ttu-id="4ebf0-111">Hodnota vlastnosti <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> se vztahuje pouze na řádky v odstavci, které jsou zabaleny pod prvním řádkem.</span><span class="sxs-lookup"><span data-stu-id="4ebf0-111">The value of the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property only applies to lines in a paragraph that have wrapped below the first line.</span></span>  
  
3. <span data-ttu-id="4ebf0-112">Nastavte vlastnost <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> na celé číslo představující vzdálenost v pixelech mezi pravým okrajem ovládacího prvku a pravým okrajem textu.</span><span class="sxs-lookup"><span data-stu-id="4ebf0-112">Set the <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> property to an integer representing the distance in pixels between the right edge of the control and the right edge of the text.</span></span>  
  
    ```vb  
    RichTextBox1.SelectionIndent = 8  
    RichTextBox1.SelectionHangingIndent = 3  
    RichTextBox1.SelectionRightIndent = 12  
    ```  
  
    ```csharp  
    richTextBox1.SelectionIndent = 8;  
    richTextBox1.SelectionHangingIndent = 3;  
    richTextBox1.SelectionRightIndent = 12;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionIndent = 8;  
    richTextBox1->SelectionHangingIndent = 3;  
    richTextBox1->SelectionRightIndent = 12;  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="4ebf0-113">Všechny tyto vlastnosti mají vliv na všechny odstavce obsahující vybraný text a také na text, který je zadán po aktuálním místě vložení.</span><span class="sxs-lookup"><span data-stu-id="4ebf0-113">All these properties affect any paragraphs that contain selected text, and also the text that is typed after the current insertion point.</span></span> <span data-ttu-id="4ebf0-114">Když třeba uživatel vybere slovo v rámci odstavce a pak upraví odsazení, bude se nové nastavení vztahovat na celý odstavec, který obsahuje toto slovo, a také na jakékoli odstavce, které se následně zadaly po vybraném odstavci.</span><span class="sxs-lookup"><span data-stu-id="4ebf0-114">For example, when a user selects a word within a paragraph and then adjusts the indentation, the new settings will apply to the entire paragraph that contains that word, and also to any paragraphs subsequently entered after the selected paragraph.</span></span> <span data-ttu-id="4ebf0-115">Informace o tom, jak text programově vybírat, najdete v tématu <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="4ebf0-115">For information about selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ebf0-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ebf0-116">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="4ebf0-117">Ovládací prvek RichTextBox</span><span class="sxs-lookup"><span data-stu-id="4ebf0-117">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="4ebf0-118">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4ebf0-118">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
