---
title: 'Postupy: Poskytnutí dialogového okna průběhu pro operace se soubory (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: e48fcee8dc4c85083a00a89c88027529ab1cc3aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>Postupy: Poskytnutí dialogového okna průběhu pro operace se soubory (Průvodce programováním v C#)
Můžete zadat standardní dialogové okno se zobrazí průběh na operací se soubory v systému Windows, pokud použijete <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> metoda v <xref:Microsoft.VisualBasic?displayProperty=nameWithType> oboru názvů.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a>Chcete-li přidat odkaz v sadě Visual Studio  
  
1.  Na řádku nabídek zvolte **projektu**, **přidat odkaz na**.  
  
     **Správce odkazů** zobrazí se dialogové okno.  
  
2.  V **sestavení** oblasti, zvolte**Framework** Pokud již není vybraná.  
  
3.  V seznamu názvů, vyberte **Microsoft.VisualBasic –** zaškrtněte políčko a potom vyberte **OK** tlačítko dialogové okno zavřete.  
  
## <a name="example"></a>Příklad  
 Následující kód zkopíruje adresáři, `sourcePath` určuje do adresáře, `destinationPath` určuje. Tento kód také poskytuje standardní dialogové okno se zobrazí odhadované částky zbývající čas předtím, než se dokončí operaci.  
  
 [!code-csharp[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Systém souborů a registr (C# Průvodce programováním)](../../../csharp/programming-guide/file-system/index.md)
