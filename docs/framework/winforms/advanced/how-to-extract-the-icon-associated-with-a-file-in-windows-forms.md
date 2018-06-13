---
title: 'Postupy: Extrahování ikony přidružené k souboru v rozhraní Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: 21bce2f630649afb59272362a7f40055855ed512
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522663"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a><span data-ttu-id="76b08-102">Postupy: Extrahování ikony přidružené k souboru v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="76b08-102">How to: Extract the Icon Associated with a File in Windows Forms</span></span>
<span data-ttu-id="76b08-103">Mnoho soubory s vloženými ikony, které poskytují vizuální reprezentace přidružený soubor typu.</span><span class="sxs-lookup"><span data-stu-id="76b08-103">Many files have embedded icons that provide a visual representation of the associated file type.</span></span> <span data-ttu-id="76b08-104">Například aplikace Microsoft Word dokumenty obsahují ikonu, která je identifikuje jako dokumenty aplikace Word.</span><span class="sxs-lookup"><span data-stu-id="76b08-104">For example, Microsoft Word documents contain an icon that identifies them as Word documents.</span></span> <span data-ttu-id="76b08-105">Při zobrazení souborů do ovládacího prvku seznam nebo ovládací prvek tabulky, můžete zobrazit na ikonu představující typ souboru vedle názvu každého souboru.</span><span class="sxs-lookup"><span data-stu-id="76b08-105">When displaying files in a list control or table control, you may want to display the icon representing the file type next to each file name.</span></span> <span data-ttu-id="76b08-106">To můžete provést snadno pomocí <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="76b08-106">You can do this easily by using the <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76b08-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="76b08-107">Example</span></span>  
 <span data-ttu-id="76b08-108">Následující příklad kódu ukazuje, jak extrahování ikony přidružené k souboru a název souboru a jeho přidružené ikony v zobrazení <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="76b08-108">The following code example demonstrates how to extract the icon associated with a file and display the file name and its associated icon in a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="76b08-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="76b08-109">Compiling the Code</span></span>  
 <span data-ttu-id="76b08-110">Ke kompilaci v příkladu:</span><span class="sxs-lookup"><span data-stu-id="76b08-110">To compile the example:</span></span>  
  
-   <span data-ttu-id="76b08-111">Předchozí kód vložte do formuláře Windows a volání `ExtractAssociatedIconExample` metoda z konstruktoru formuláře nebo <xref:System.Windows.Forms.Form.Load> metoda zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="76b08-111">Paste the preceding code into a Windows Form, and call the `ExtractAssociatedIconExample` method from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     <span data-ttu-id="76b08-112">Je nutné zajistit, že importuje svého formuláře <xref:System.IO> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="76b08-112">You will need to make sure that your form imports the <xref:System.IO> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76b08-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="76b08-113">See Also</span></span>  
 [<span data-ttu-id="76b08-114">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="76b08-114">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="76b08-115">Ovládací prvek ListView</span><span class="sxs-lookup"><span data-stu-id="76b08-115">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
