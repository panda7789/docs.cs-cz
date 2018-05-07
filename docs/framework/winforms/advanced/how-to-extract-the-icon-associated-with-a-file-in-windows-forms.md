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
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a>Postupy: Extrahování ikony přidružené k souboru v rozhraní Windows Forms
Mnoho soubory s vloženými ikony, které poskytují vizuální reprezentace přidružený soubor typu. Například aplikace Microsoft Word dokumenty obsahují ikonu, která je identifikuje jako dokumenty aplikace Word. Při zobrazení souborů do ovládacího prvku seznam nebo ovládací prvek tabulky, můžete zobrazit na ikonu představující typ souboru vedle názvu každého souboru. To můžete provést snadno pomocí <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> metoda.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak extrahování ikony přidružené k souboru a název souboru a jeho přidružené ikony v zobrazení <xref:System.Windows.Forms.ListView> ovládacího prvku.  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Ke kompilaci v příkladu:  
  
-   Předchozí kód vložte do formuláře Windows a volání `ExtractAssociatedIconExample` metoda z konstruktoru formuláře nebo <xref:System.Windows.Forms.Form.Load> metoda zpracování událostí.  
  
     Je nutné zajistit, že importuje svého formuláře <xref:System.IO> oboru názvů.  
  
## <a name="see-also"></a>Viz také  
 [Obrázky, rastrové obrázky a metasoubory](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Ovládací prvek ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
