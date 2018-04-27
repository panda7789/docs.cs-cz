---
title: 'Postupy: Sdílení připojených dat mezi formuláři pomocí součásti BindingSource'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1907f25e2d9bfe5fc6e93020add47d8a52379e87
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a>Postupy: Sdílení připojených dat mezi formuláři pomocí součásti BindingSource
Můžete snadno sdílet data mezi formuláři pomocí <xref:System.Windows.Forms.BindingSource> součásti. Můžete například zobrazit jednu jen pro čtení formulář, který je souhrn dat zdroje dat a jiné upravovat formulář, který obsahuje podrobné informace o aktuálně vybrané položky ve zdroji dat. Tento příklad ukazuje tento scénář.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak sdílet <xref:System.Windows.Forms.BindingSource> a vázaných dat mezi formuláři. V tomto příkladu sdílený <xref:System.Windows.Forms.BindingSource> předaný do konstruktoru objektu podřízené formuláře. Podřízené formuláře umožňuje uživateli upravit data pro aktuálně vybrané položky na hlavní formulář.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.BindingSource.BindingComplete> Událost pro <xref:System.Windows.Forms.BindingSource> součást zpracovává v příkladu zajistit, aby zůstaly synchronizované dva formuláře. Další informace o tom, proč je to provést, najdete v části [postupy: Zajistěte více ovládací prvky vázané stejné Data zdroje zůstávají synchronizovat](../../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md).  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Windows.Forms, System.Drawing, System.Data a System.Xml sestavení.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 [Komponenta BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Windows Forms – datová vazba](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Postupy: Zpracování chyb a výjimek, k nimž došlo v souvislosti s datovou vazbou](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
