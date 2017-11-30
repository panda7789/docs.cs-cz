---
title: "Postupy: Nastavení odsazení, ukotvených odsazení a odstavců s odrážkami pomocí ovládacího prvku Windows Forms RichTextBox"
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
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], setting indents
- .rtf files [Windows Forms], formatting in RichTextBox control
- examples [Windows Forms], text boxes
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting indents and bullets
- text boxes [Windows Forms], bullets
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9b1398c0438f9ebe528e9394014f5f6529ea8f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="ef376-102">Postupy: Nastavení odsazení, ukotvených odsazení a odstavců s odrážkami pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="ef376-102">How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="ef376-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> spoustu možností pro formátování textu, zobrazí se má ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="ef376-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="ef376-104">Vybrané odstavce dokáže formátovat jako seznamy s odrážkami nastavením <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ef376-104">You can format selected paragraphs as bulleted lists by setting the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property.</span></span> <span data-ttu-id="ef376-105">Můžete také <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, a <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> vlastnosti, které chcete nastavit odsazení odstavce vzhledem ke levé a pravé hrany ovládacího prvku a levý okraj dalších řádků textu.</span><span class="sxs-lookup"><span data-stu-id="ef376-105">You can also use the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, and <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> properties to set the indentation of paragraphs relative to the left and right edges of the control, and the left edge of other lines of text.</span></span>  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a><span data-ttu-id="ef376-106">Formátování odstavce jako seznam s odrážkami</span><span class="sxs-lookup"><span data-stu-id="ef376-106">To format a paragraph as a bulleted list</span></span>  
  
1.  <span data-ttu-id="ef376-107">Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="ef376-107">Set the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property to `true`.</span></span>  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### <a name="to-indent-a-paragraph"></a><span data-ttu-id="ef376-108">Odsazení odstavce</span><span class="sxs-lookup"><span data-stu-id="ef376-108">To indent a paragraph</span></span>  
  
1.  <span data-ttu-id="ef376-109">Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> vlastnost na celé číslo představující vzdálenost v pixelech mezi levým okrajem ovládacího prvku a levém okraji textu.</span><span class="sxs-lookup"><span data-stu-id="ef376-109">Set the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> property to an integer representing the distance in pixels between the left edge of the control and the left edge of the text.</span></span>  
  
2.  <span data-ttu-id="ef376-110">Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> vlastnost na celé číslo představující vzdálenost v pixelech mezi levý okraj prvního řádku text odstavce a levý okraj následující řádky ve stejné odstavce.</span><span class="sxs-lookup"><span data-stu-id="ef376-110">Set the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property to an integer representing the distance in pixels between the left edge of the first line of text in the paragraph and the left edge of subsequent lines in the same paragraph.</span></span> <span data-ttu-id="ef376-111">Hodnota <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> vlastnost se vztahuje jenom na řádky v odstavci, které mají zabalené pod první řádek.</span><span class="sxs-lookup"><span data-stu-id="ef376-111">The value of the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property only applies to lines in a paragraph that have wrapped below the first line.</span></span>  
  
3.  <span data-ttu-id="ef376-112">Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> vlastnost na celé číslo představující vzdálenost v pixelech mezi pravým okrajem ovládacího prvku a pravý okraj textu.</span><span class="sxs-lookup"><span data-stu-id="ef376-112">Set the <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> property to an integer representing the distance in pixels between the right edge of the control and the right edge of the text.</span></span>  
  
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
    >  <span data-ttu-id="ef376-113">Všechny tyto vlastnosti ovlivňují všechny odstavců, které obsahují vybraný text a také text, který je zadán po aktuální kurzor.</span><span class="sxs-lookup"><span data-stu-id="ef376-113">All these properties affect any paragraphs that contain selected text, and also the text that is typed after the current insertion point.</span></span> <span data-ttu-id="ef376-114">Například pokud uživatel vybere možnost aplikace word v rámci odstavce a pak upraví odsazení, nové nastavení bude použito na celý odstavec, který obsahuje aplikace word a také na všechny odstavce následně zadali po vybraného odstavce.</span><span class="sxs-lookup"><span data-stu-id="ef376-114">For example, when a user selects a word within a paragraph and then adjusts the indentation, the new settings will apply to the entire paragraph that contains that word, and also to any paragraphs subsequently entered after the selected paragraph.</span></span> <span data-ttu-id="ef376-115">Informace o výběr textu pomocí programu najdete v tématu <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef376-115">For information about selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef376-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef376-116">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="ef376-117">RichTextBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="ef376-117">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="ef376-118">Ovládací prvky používané ve formulářích Windows</span><span class="sxs-lookup"><span data-stu-id="ef376-118">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
