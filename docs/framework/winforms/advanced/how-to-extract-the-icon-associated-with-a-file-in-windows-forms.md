---
title: 'Postupy: Extrahování ikony přidružené k souboru v modelu Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: d754dc5e8a57b3c4e2e5439bb2524a22d44813c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112551"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a><span data-ttu-id="b4f53-102">Postupy: Extrahování ikony přidružené k souboru v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b4f53-102">How to: Extract the Icon Associated with a File in Windows Forms</span></span>
<span data-ttu-id="b4f53-103">Mnoho souborů s vloženými ikony, které poskytují vizuální znázornění přidružený soubor typu.</span><span class="sxs-lookup"><span data-stu-id="b4f53-103">Many files have embedded icons that provide a visual representation of the associated file type.</span></span> <span data-ttu-id="b4f53-104">Například Microsoft Word dokumenty obsahují ikonu, která je identifikuje jako dokumentů aplikace Word.</span><span class="sxs-lookup"><span data-stu-id="b4f53-104">For example, Microsoft Word documents contain an icon that identifies them as Word documents.</span></span> <span data-ttu-id="b4f53-105">Při zobrazování souborů do ovládacího prvku seznamu nebo ovládacího prvku tabulky, můžete zobrazit ikonu představující typ souboru vedle názvu každého souboru.</span><span class="sxs-lookup"><span data-stu-id="b4f53-105">When displaying files in a list control or table control, you may want to display the icon representing the file type next to each file name.</span></span> <span data-ttu-id="b4f53-106">Můžete to provést jednoduše pomocí <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b4f53-106">You can do this easily by using the <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4f53-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="b4f53-107">Example</span></span>  
 <span data-ttu-id="b4f53-108">Následující příklad kódu ukazuje, jak k extrahování ikony přidružené k souboru a zobrazení názvu souboru a jeho přidružené ikonu v <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b4f53-108">The following code example demonstrates how to extract the icon associated with a file and display the file name and its associated icon in a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b4f53-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b4f53-109">Compiling the Code</span></span>  
 <span data-ttu-id="b4f53-110">Chcete-li příklad zkompilovat:</span><span class="sxs-lookup"><span data-stu-id="b4f53-110">To compile the example:</span></span>  
  
-   <span data-ttu-id="b4f53-111">Předchozí kód vložte do formuláře Windows a volání `ExtractAssociatedIconExample` metodu z konstruktoru formuláře nebo <xref:System.Windows.Forms.Form.Load> metody zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="b4f53-111">Paste the preceding code into a Windows Form, and call the `ExtractAssociatedIconExample` method from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     <span data-ttu-id="b4f53-112">Budete muset Ujistěte se, že váš formulář importuje <xref:System.IO> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b4f53-112">You will need to make sure that your form imports the <xref:System.IO> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4f53-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4f53-113">See also</span></span>

- [<span data-ttu-id="b4f53-114">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="b4f53-114">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="b4f53-115">ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="b4f53-115">ListView Control</span></span>](../controls/listview-control-windows-forms.md)
