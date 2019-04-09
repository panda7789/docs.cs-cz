---
title: 'Postupy: Nastavení odsazení, předsazení a odstavců s odrážkami pomocí ovládacího prvku Windows Forms RichTextBox'
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
ms.openlocfilehash: 4cb9b351b5ed1ab9cd05be0763d967000791fb46
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140644"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="d9f01-102">Postupy: Nastavení odsazení, předsazení a odstavců s odrážkami pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="d9f01-102">How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="d9f01-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> ovládací prvek má mnoho možností pro formátování textu se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="d9f01-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="d9f01-104">Vybrané odstavce jako seznamy s odrážkami můžete naformátovat tak, že nastavíte <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d9f01-104">You can format selected paragraphs as bulleted lists by setting the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property.</span></span> <span data-ttu-id="d9f01-105">Můžete také použít <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, a <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> vlastnosti nastavení odsazení odstavce doleva a pravého okraje ovládacího prvku a levým okrajem dalších řádků textu.</span><span class="sxs-lookup"><span data-stu-id="d9f01-105">You can also use the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, and <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> properties to set the indentation of paragraphs relative to the left and right edges of the control, and the left edge of other lines of text.</span></span>  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a><span data-ttu-id="d9f01-106">K formátování odstavce jako seznam s odrážkami</span><span class="sxs-lookup"><span data-stu-id="d9f01-106">To format a paragraph as a bulleted list</span></span>  
  
1.  <span data-ttu-id="d9f01-107">Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="d9f01-107">Set the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property to `true`.</span></span>  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### <a name="to-indent-a-paragraph"></a><span data-ttu-id="d9f01-108">Odsazení odstavce</span><span class="sxs-lookup"><span data-stu-id="d9f01-108">To indent a paragraph</span></span>  
  
1.  <span data-ttu-id="d9f01-109">Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> vlastnost na celé číslo představující vzdálenost v pixelech mezi levým okrajem ovládacího prvku a levým okrajem text.</span><span class="sxs-lookup"><span data-stu-id="d9f01-109">Set the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> property to an integer representing the distance in pixels between the left edge of the control and the left edge of the text.</span></span>  
  
2.  <span data-ttu-id="d9f01-110">Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> vlastnost na celé číslo představující vzdálenost v pixelech mezi levým okrajem první řádek textu odstavce a levým okrajem následující řádky ve stejném paragraph.</span><span class="sxs-lookup"><span data-stu-id="d9f01-110">Set the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property to an integer representing the distance in pixels between the left edge of the first line of text in the paragraph and the left edge of subsequent lines in the same paragraph.</span></span> <span data-ttu-id="d9f01-111">Hodnota <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> vlastnost platí jenom pro řádky v odstavci zabalené pod první řádek.</span><span class="sxs-lookup"><span data-stu-id="d9f01-111">The value of the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property only applies to lines in a paragraph that have wrapped below the first line.</span></span>  
  
3.  <span data-ttu-id="d9f01-112">Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> vlastnost na celé číslo představující vzdálenost v pixelech mezi pravým okrajem ovládacího prvku a pravým okrajem text.</span><span class="sxs-lookup"><span data-stu-id="d9f01-112">Set the <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> property to an integer representing the distance in pixels between the right edge of the control and the right edge of the text.</span></span>  
  
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
    >  <span data-ttu-id="d9f01-113">Všechny tyto vlastnosti ovlivňují všechny odstavce, které obsahují vybraný text a také text, který je zadán po do aktuálního místa vložení.</span><span class="sxs-lookup"><span data-stu-id="d9f01-113">All these properties affect any paragraphs that contain selected text, and also the text that is typed after the current insertion point.</span></span> <span data-ttu-id="d9f01-114">Například když uživatel vybere slova v rámci odstavce a poté nastaví odsazení, nové nastavení bude použito celý odstavec obsahující toto slovo a také všechny odstavce následně zadaných po vybraný odstavec.</span><span class="sxs-lookup"><span data-stu-id="d9f01-114">For example, when a user selects a word within a paragraph and then adjusts the indentation, the new settings will apply to the entire paragraph that contains that word, and also to any paragraphs subsequently entered after the selected paragraph.</span></span> <span data-ttu-id="d9f01-115">Informace o výběr textu pomocí programu najdete v tématu <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="d9f01-115">For information about selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9f01-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9f01-116">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="d9f01-117">Ovládací prvek RichTextBox</span><span class="sxs-lookup"><span data-stu-id="d9f01-117">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="d9f01-118">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d9f01-118">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
