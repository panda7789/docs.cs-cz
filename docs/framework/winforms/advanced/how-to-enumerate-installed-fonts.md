---
title: "Postupy: Výčet instalovaných písem"
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
helpviewer_keywords:
- fonts [Windows Forms], enumerating installed
- examples [Windows Forms], fonts
ms.assetid: 26d74ef5-0f39-4eeb-8d20-00e66e014abe
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 905b5ecbda58d2f7edb7fc30d5505eec63a64c2b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enumerate-installed-fonts"></a><span data-ttu-id="181aa-102">Postupy: Výčet instalovaných písem</span><span class="sxs-lookup"><span data-stu-id="181aa-102">How to: Enumerate Installed Fonts</span></span>
<span data-ttu-id="181aa-103"><xref:System.Drawing.Text.InstalledFontCollection> Třída dědí z <xref:System.Drawing.Text.FontCollection> abstraktní základní třída.</span><span class="sxs-lookup"><span data-stu-id="181aa-103">The <xref:System.Drawing.Text.InstalledFontCollection> class inherits from the <xref:System.Drawing.Text.FontCollection> abstract base class.</span></span> <span data-ttu-id="181aa-104">Můžete použít <xref:System.Drawing.Text.InstalledFontCollection> objekt, který chcete vytvořit výčet písem v počítači nainstalována.</span><span class="sxs-lookup"><span data-stu-id="181aa-104">You can use an <xref:System.Drawing.Text.InstalledFontCollection> object to enumerate the fonts installed on the computer.</span></span> <span data-ttu-id="181aa-105"><xref:System.Drawing.Text.FontCollection.Families%2A> Vlastnost <xref:System.Drawing.Text.InstalledFontCollection> objekt je pole <xref:System.Drawing.FontFamily> objekty.</span><span class="sxs-lookup"><span data-stu-id="181aa-105">The <xref:System.Drawing.Text.FontCollection.Families%2A> property of an <xref:System.Drawing.Text.InstalledFontCollection> object is an array of <xref:System.Drawing.FontFamily> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="181aa-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="181aa-106">Example</span></span>  
 <span data-ttu-id="181aa-107">Následující příklad uvádí názvy rodiny písem v počítači nainstalována.</span><span class="sxs-lookup"><span data-stu-id="181aa-107">The following example lists the names of all the font families installed on the computer.</span></span> <span data-ttu-id="181aa-108">Kód načte <xref:System.Drawing.FontFamily.Name%2A> vlastnost jednotlivých <xref:System.Drawing.FontFamily> objekt v poli vráceném <xref:System.Drawing.Text.FontCollection.Families%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="181aa-108">The code retrieves the <xref:System.Drawing.FontFamily.Name%2A> property of each <xref:System.Drawing.FontFamily> object in the array returned by the <xref:System.Drawing.Text.FontCollection.Families%2A> property.</span></span> <span data-ttu-id="181aa-109">Jako jsou načteny názvů rodin, jsou zřetězen do seznamu formuláře oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="181aa-109">As the family names are retrieved, they are concatenated to form a comma-separated list.</span></span> <span data-ttu-id="181aa-110">Pak se <xref:System.Drawing.Graphics.DrawString%2A> metodu <xref:System.Drawing.Graphics> třída nevykresluje v obdélníku seznam oddělený čárkami.</span><span class="sxs-lookup"><span data-stu-id="181aa-110">Then the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class draws the comma-separated list in a rectangle.</span></span>  
  
 <span data-ttu-id="181aa-111">Pokud spustíte příklad kódu, bude výstup podobný zobrazená na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="181aa-111">If you run the example code, the output will be similar to that shown in the following illustration.</span></span>  
  
 <span data-ttu-id="181aa-112">![Nainstalovat písem](../../../../docs/framework/winforms/advanced/media/csfontstext6.png "csfontstext6")</span><span class="sxs-lookup"><span data-stu-id="181aa-112">![Installed Fonts](../../../../docs/framework/winforms/advanced/media/csfontstext6.png "csfontstext6")</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.FontsAndText#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="181aa-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="181aa-113">Compiling the Code</span></span>  
 <span data-ttu-id="181aa-114">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="181aa-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span> <span data-ttu-id="181aa-115">Kromě toho by měla importovat <xref:System.Drawing.Text> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="181aa-115">In addition, you should import the <xref:System.Drawing.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="181aa-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="181aa-116">See Also</span></span>  
 [<span data-ttu-id="181aa-117">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="181aa-117">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
