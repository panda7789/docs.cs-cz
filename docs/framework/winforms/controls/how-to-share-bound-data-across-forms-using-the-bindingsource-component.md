---
title: 'Postupy: Sdílení vázaných dat mezi formuláři pomocí komponenty BindingSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
ms.openlocfilehash: aa497194fd4ac65f48773a45175333a1d862b453
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956077"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a>Postupy: Sdílení vázaných dat mezi formuláři pomocí komponenty BindingSource
Data můžete v různých formulářích snadno sdílet pomocí <xref:System.Windows.Forms.BindingSource> komponenty. Například můžete chtít zobrazit jeden formulář jen pro čtení, který shrnuje data zdrojů dat a další Upravitelný formulář, který obsahuje podrobné informace o aktuálně vybrané položce ve zdroji dat. Tento příklad ukazuje tento scénář.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak sdílet <xref:System.Windows.Forms.BindingSource> a jeho vázaná data napříč formuláři. V tomto příkladu je sdílena <xref:System.Windows.Forms.BindingSource> předána konstruktoru podřízeného formuláře. Podřízený formulář umožňuje uživateli upravovat data pro aktuálně vybranou položku v hlavním formuláři.  
  
> [!NOTE]
> <xref:System.Windows.Forms.BindingSource.BindingComplete> Událost<xref:System.Windows.Forms.BindingSource> pro komponentu je zpracována v příkladu, aby bylo zajištěno, že obě formy budou synchronizovány. Další informace o tom, proč je to hotové [, najdete v tématu How to: Zajistěte, aby více ovládacích prvků vázaných na](../multiple-controls-bound-to-data-source-synchronized.md)stejný zdroj dat zůstaly synchronizované.  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. Windows. Forms, System. Drawing, System. data a System. XML.  
  
## <a name="see-also"></a>Viz také:

- [Komponenta BindingSource](bindingsource-component.md)
- [Windows Forms – datová vazba](../windows-forms-data-binding.md)
- [Postupy: Zpracování chyb a výjimek, ke kterým dochází s datovou vazbou](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
