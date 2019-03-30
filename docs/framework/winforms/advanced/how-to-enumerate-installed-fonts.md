---
title: 'Postupy: Výčet instalovaných písem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], enumerating installed
- examples [Windows Forms], fonts
ms.assetid: 26d74ef5-0f39-4eeb-8d20-00e66e014abe
ms.openlocfilehash: e56f06d6f7a762a1ef1ff85fa30751ea64f9f14b
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653740"
---
# <a name="how-to-enumerate-installed-fonts"></a><span data-ttu-id="6ba27-102">Postupy: Výčet instalovaných písem</span><span class="sxs-lookup"><span data-stu-id="6ba27-102">How to: Enumerate Installed Fonts</span></span>
<span data-ttu-id="6ba27-103"><xref:System.Drawing.Text.InstalledFontCollection> Třída dědí z <xref:System.Drawing.Text.FontCollection> abstraktní základní třída.</span><span class="sxs-lookup"><span data-stu-id="6ba27-103">The <xref:System.Drawing.Text.InstalledFontCollection> class inherits from the <xref:System.Drawing.Text.FontCollection> abstract base class.</span></span> <span data-ttu-id="6ba27-104">Můžete použít <xref:System.Drawing.Text.InstalledFontCollection> objekt výčet písem v počítači nainstalována.</span><span class="sxs-lookup"><span data-stu-id="6ba27-104">You can use an <xref:System.Drawing.Text.InstalledFontCollection> object to enumerate the fonts installed on the computer.</span></span> <span data-ttu-id="6ba27-105"><xref:System.Drawing.Text.FontCollection.Families%2A> Vlastnost <xref:System.Drawing.Text.InstalledFontCollection> objektu je pole <xref:System.Drawing.FontFamily> objekty.</span><span class="sxs-lookup"><span data-stu-id="6ba27-105">The <xref:System.Drawing.Text.FontCollection.Families%2A> property of an <xref:System.Drawing.Text.InstalledFontCollection> object is an array of <xref:System.Drawing.FontFamily> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ba27-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ba27-106">Example</span></span>  
 <span data-ttu-id="6ba27-107">Následující příklad zobrazí seznam názvů rodin písem v počítači nainstalována.</span><span class="sxs-lookup"><span data-stu-id="6ba27-107">The following example lists the names of all the font families installed on the computer.</span></span> <span data-ttu-id="6ba27-108">Kód načte <xref:System.Drawing.FontFamily.Name%2A> vlastnosti každého <xref:System.Drawing.FontFamily> objekt v poli vrácené <xref:System.Drawing.Text.FontCollection.Families%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6ba27-108">The code retrieves the <xref:System.Drawing.FontFamily.Name%2A> property of each <xref:System.Drawing.FontFamily> object in the array returned by the <xref:System.Drawing.Text.FontCollection.Families%2A> property.</span></span> <span data-ttu-id="6ba27-109">Protože jsou načteny názvy rodiny, jsou zřetězeny do formuláře čárkou oddělený seznam.</span><span class="sxs-lookup"><span data-stu-id="6ba27-109">As the family names are retrieved, they are concatenated to form a comma-separated list.</span></span> <span data-ttu-id="6ba27-110">Pak bude <xref:System.Drawing.Graphics.DrawString%2A> metodu <xref:System.Drawing.Graphics> třídy kreslení v obdélníku seznam oddělený čárkami.</span><span class="sxs-lookup"><span data-stu-id="6ba27-110">Then the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class draws the comma-separated list in a rectangle.</span></span>  
  
 <span data-ttu-id="6ba27-111">Pokud spustíte příklad kódu, výstup bude podobný tomu je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="6ba27-111">If you run the example code, the output will be similar to that shown in the following illustration:</span></span>  
  
 ![Snímek obrazovky zobrazující rodin písem nainstalované.](./media/how-to-enumerate-installed-fonts/list-installed-font-families.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.FontsAndText#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6ba27-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6ba27-113">Compiling the Code</span></span>  
 <span data-ttu-id="6ba27-114">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="6ba27-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span> <span data-ttu-id="6ba27-115">Kromě toho byste měli importovat <xref:System.Drawing.Text> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6ba27-115">In addition, you should import the <xref:System.Drawing.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ba27-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ba27-116">See also</span></span>
- [<span data-ttu-id="6ba27-117">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="6ba27-117">Using Fonts and Text</span></span>](using-fonts-and-text.md)
