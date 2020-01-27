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
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a>Postupy: Extrahování ikony přidružené k souboru v rozhraní Windows Forms
Mnoho souborů má vložené ikony, které poskytují vizuální znázornění přidruženého typu souboru. Například dokumenty aplikace Microsoft Word obsahují ikonu, která je identifikuje jako dokumenty aplikace Word. Při zobrazování souborů v ovládacím prvku seznam nebo v ovládacím prvku tabulka můžete chtít zobrazit ikonu představující typ souboru vedle každého názvu souboru. To lze provést snadno pomocí metody <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak extrahovat ikonu přidruženou k souboru a zobrazit název souboru a jeho přidruženou ikonu v ovládacím prvku <xref:System.Windows.Forms.ListView>.  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Chcete-li zkompilovat příklad:  
  
- Vložte předchozí kód do formuláře Windows a zavolejte metodu `ExtractAssociatedIconExample` z konstruktoru formuláře nebo metody zpracování událostí <xref:System.Windows.Forms.Form.Load>.  
  
     Bude nutné zajistit, aby formulář naimportoval <xref:System.IO> obor názvů.  
  
## <a name="see-also"></a>Viz také:

- [Obrázky, rastrové obrázky a metasoubory](images-bitmaps-and-metafiles.md)
- [Ovládací prvek ListView](../controls/listview-control-windows-forms.md)
