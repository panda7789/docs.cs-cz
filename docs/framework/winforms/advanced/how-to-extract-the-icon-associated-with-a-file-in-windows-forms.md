---
title: 'Postupy: extrakce ikony přidružené k souboru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: 28769144b0e1c631a31c3c541747a6215f861d0e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742538"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a><span data-ttu-id="89f3d-102">Postupy: Extrahování ikony přidružené k souboru v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="89f3d-102">How to: Extract the Icon Associated with a File in Windows Forms</span></span>
<span data-ttu-id="89f3d-103">Mnoho souborů má vložené ikony, které poskytují vizuální znázornění přidruženého typu souboru.</span><span class="sxs-lookup"><span data-stu-id="89f3d-103">Many files have embedded icons that provide a visual representation of the associated file type.</span></span> <span data-ttu-id="89f3d-104">Například dokumenty aplikace Microsoft Word obsahují ikonu, která je identifikuje jako dokumenty aplikace Word.</span><span class="sxs-lookup"><span data-stu-id="89f3d-104">For example, Microsoft Word documents contain an icon that identifies them as Word documents.</span></span> <span data-ttu-id="89f3d-105">Při zobrazování souborů v ovládacím prvku seznam nebo v ovládacím prvku tabulka můžete chtít zobrazit ikonu představující typ souboru vedle každého názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="89f3d-105">When displaying files in a list control or table control, you may want to display the icon representing the file type next to each file name.</span></span> <span data-ttu-id="89f3d-106">To lze provést snadno pomocí metody <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A>.</span><span class="sxs-lookup"><span data-stu-id="89f3d-106">You can do this easily by using the <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89f3d-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="89f3d-107">Example</span></span>  
 <span data-ttu-id="89f3d-108">Následující příklad kódu ukazuje, jak extrahovat ikonu přidruženou k souboru a zobrazit název souboru a jeho přidruženou ikonu v ovládacím prvku <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="89f3d-108">The following code example demonstrates how to extract the icon associated with a file and display the file name and its associated icon in a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="89f3d-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="89f3d-109">Compiling the Code</span></span>  
 <span data-ttu-id="89f3d-110">Chcete-li zkompilovat příklad:</span><span class="sxs-lookup"><span data-stu-id="89f3d-110">To compile the example:</span></span>  
  
- <span data-ttu-id="89f3d-111">Vložte předchozí kód do formuláře Windows a zavolejte metodu `ExtractAssociatedIconExample` z konstruktoru formuláře nebo metody zpracování událostí <xref:System.Windows.Forms.Form.Load>.</span><span class="sxs-lookup"><span data-stu-id="89f3d-111">Paste the preceding code into a Windows Form, and call the `ExtractAssociatedIconExample` method from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     <span data-ttu-id="89f3d-112">Bude nutné zajistit, aby formulář naimportoval <xref:System.IO> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="89f3d-112">You will need to make sure that your form imports the <xref:System.IO> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89f3d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89f3d-113">See also</span></span>

- [<span data-ttu-id="89f3d-114">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="89f3d-114">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="89f3d-115">Ovládací prvek ListView</span><span class="sxs-lookup"><span data-stu-id="89f3d-115">ListView Control</span></span>](../controls/listview-control-windows-forms.md)
