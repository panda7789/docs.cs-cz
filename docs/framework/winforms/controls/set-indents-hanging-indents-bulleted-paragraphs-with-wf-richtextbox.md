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
ms.openlocfilehash: 9d095e3561cd346e6dbd99d1be7468f6ad5725a6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960457"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="8faf9-102">Postupy: Nastavení odsazení, předsazení a odstavců s odrážkami pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="8faf9-102">How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="8faf9-103">Ovládací prvek <xref:System.Windows.Forms.RichTextBox> model Windows Forms má mnoho možností formátování textu, který zobrazuje.</span><span class="sxs-lookup"><span data-stu-id="8faf9-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="8faf9-104">Vybrané odstavce můžete formátovat jako seznamy s odrážkami nastavením <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8faf9-104">You can format selected paragraphs as bulleted lists by setting the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property.</span></span> <span data-ttu-id="8faf9-105">Pomocí <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>vlastností, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>a <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> můžete také nastavit odsazení odstavců vzhledem k levému a pravému okraji ovládacího prvku a levý okraj dalších řádků textu.</span><span class="sxs-lookup"><span data-stu-id="8faf9-105">You can also use the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, and <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> properties to set the indentation of paragraphs relative to the left and right edges of the control, and the left edge of other lines of text.</span></span>  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a><span data-ttu-id="8faf9-106">Formátování odstavce jako seznamu s odrážkami</span><span class="sxs-lookup"><span data-stu-id="8faf9-106">To format a paragraph as a bulleted list</span></span>  
  
1. <span data-ttu-id="8faf9-107">Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="8faf9-107">Set the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property to `true`.</span></span>  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### <a name="to-indent-a-paragraph"></a><span data-ttu-id="8faf9-108">Odsazení odstavce</span><span class="sxs-lookup"><span data-stu-id="8faf9-108">To indent a paragraph</span></span>  
  
1. <span data-ttu-id="8faf9-109"><xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> Nastavte vlastnost na celé číslo představující vzdálenost v pixelech mezi levým okrajem ovládacího prvku a levým okrajem textu.</span><span class="sxs-lookup"><span data-stu-id="8faf9-109">Set the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> property to an integer representing the distance in pixels between the left edge of the control and the left edge of the text.</span></span>  
  
2. <span data-ttu-id="8faf9-110"><xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> Nastavte vlastnost na celé číslo představující vzdálenost v pixelech mezi levým okrajem prvního řádku textu v odstavci a levým okrajem dalších řádků ve stejném odstavci.</span><span class="sxs-lookup"><span data-stu-id="8faf9-110">Set the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property to an integer representing the distance in pixels between the left edge of the first line of text in the paragraph and the left edge of subsequent lines in the same paragraph.</span></span> <span data-ttu-id="8faf9-111">Hodnota <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> vlastnosti se vztahuje pouze na řádky v odstavci, které jsou zabaleny pod prvním řádkem.</span><span class="sxs-lookup"><span data-stu-id="8faf9-111">The value of the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property only applies to lines in a paragraph that have wrapped below the first line.</span></span>  
  
3. <span data-ttu-id="8faf9-112"><xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> Nastavte vlastnost na celé číslo představující vzdálenost v pixelech mezi pravým okrajem ovládacího prvku a pravým okrajem textu.</span><span class="sxs-lookup"><span data-stu-id="8faf9-112">Set the <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> property to an integer representing the distance in pixels between the right edge of the control and the right edge of the text.</span></span>  
  
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
    > <span data-ttu-id="8faf9-113">Všechny tyto vlastnosti mají vliv na všechny odstavce obsahující vybraný text a také na text, který je zadán po aktuálním místě vložení.</span><span class="sxs-lookup"><span data-stu-id="8faf9-113">All these properties affect any paragraphs that contain selected text, and also the text that is typed after the current insertion point.</span></span> <span data-ttu-id="8faf9-114">Když třeba uživatel vybere slovo v rámci odstavce a pak upraví odsazení, bude se nové nastavení vztahovat na celý odstavec, který obsahuje toto slovo, a také na jakékoli odstavce, které se následně zadaly po vybraném odstavci.</span><span class="sxs-lookup"><span data-stu-id="8faf9-114">For example, when a user selects a word within a paragraph and then adjusts the indentation, the new settings will apply to the entire paragraph that contains that word, and also to any paragraphs subsequently entered after the selected paragraph.</span></span> <span data-ttu-id="8faf9-115">Informace o tom, jak text programově vybírat <xref:System.Windows.Forms.TextBoxBase.Select%2A>, najdete v tématu.</span><span class="sxs-lookup"><span data-stu-id="8faf9-115">For information about selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8faf9-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8faf9-116">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="8faf9-117">Ovládací prvek RichTextBox</span><span class="sxs-lookup"><span data-stu-id="8faf9-117">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="8faf9-118">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8faf9-118">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
