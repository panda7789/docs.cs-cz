---
title: 'Postupy: Poskytnutí dialogového okna průběhu pro operace se soubory (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: e48fcee8dc4c85083a00a89c88027529ab1cc3aa
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960082"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>Postupy: Poskytnutí dialogového okna průběhu pro operace se soubory (Průvodce programováním v C#)
Můžete zadat standardní dialogové okno, který znázorňuje průběh operací se soubory ve Windows, pokud použijete <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> metodu <xref:Microsoft.VisualBasic?displayProperty=nameWithType> oboru názvů.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a>Chcete-li přidat odkaz v sadě Visual Studio  
  
1.  V panelu nabídky zvolte **projektu**, **přidat odkaz**.  
  
     **Správce odkazů** zobrazí se dialogové okno.  
  
2.  V **sestavení** oblasti, zvolte**Framework** Pokud není již vybrána.  
  
3.  Vyberte v seznamu názvů **Microsoft.VisualBasic** zaškrtněte políčko a klikněte na tlačítko **OK** tlačítka zavřete dialogové okno.  
  
## <a name="example"></a>Příklad  
 Následující kód zkopíruje adresář, který `sourcePath` určuje do adresáře, který `destinationPath` určuje. Tento kód také poskytuje standardní dialogové okno zobrazující odhadovanou výši zbývajícího času před dokončením operace.  
  
 [!code-csharp[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Systém souborů a registr (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md)
