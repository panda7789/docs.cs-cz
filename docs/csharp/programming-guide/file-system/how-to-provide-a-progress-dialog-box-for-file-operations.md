---
title: 'Postupy: Zadání dialogového okna průběhu pro Souborová operace – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 028e779f3cd8a17f162a79791b0c84abae14cf44
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590059"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>Postupy: Zadání dialogového okna průběhu pro operace se soubory (C# Průvodce programováním)
Můžete zadat standardní dialogové okno, které zobrazí průběh operací se soubory ve Windows, pokud použijete <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> metodu <xref:Microsoft.VisualBasic?displayProperty=nameWithType> v oboru názvů.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a>Přidání odkazu v aplikaci Visual Studio  
  
1. V panelu nabídek vyberte položku **projekt**, **Přidat odkaz**.  
  
     Zobrazí se dialogové okno **Správce odkazů** .  
  
2. V oblasti **sestavení** vyberte možnost **rozhraní** , pokud již není zvolena.  
  
3. V seznamu názvů zaškrtněte políčko **Microsoft. VisualBasic** a kliknutím na tlačítko **OK** zavřete dialogové okno.  
  
## <a name="example"></a>Příklad  
 Následující kód zkopíruje adresář, který `sourcePath` určuje do adresáře, který `destinationPath` určuje. Tento kód také obsahuje standardní dialogové okno, ve kterém se zobrazuje odhadované množství času zbývajícího před dokončením operace.  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a>Viz také:

- [Systém souborů a registr (C# Průvodce programováním)](./index.md)
