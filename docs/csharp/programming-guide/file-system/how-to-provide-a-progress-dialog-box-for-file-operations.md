---
title: Dialogové okno Průběh pro operace se soubory – Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 30ab84054d26f5b32a3f042a8d35d5ef1211d928
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705129"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>Jak poskytnout dialogové okno průběhu pro operace se soubory (Průvodce programováním jazyka C#)
Pokud použijete metodu <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> v oboru názvů, můžete zadat standardní dialogové <xref:Microsoft.VisualBasic?displayProperty=nameWithType> okno, které zobrazuje průběh operací se soubory v systému Windows.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a>Přidání odkazu v sadě Visual Studio  
  
1. Na řádku nabídek zvolte **Project**, **Add Reference**.  
  
     Zobrazí se dialogové okno **Správce odkazů.**  
  
2. V oblasti **Sestavení** zvolte **Framework,** pokud ještě není vybrána.  
  
3. V seznamu názvů zaškrtněte políčko **Microsoft.VisualBasic** a potom zvolte tlačítko **OK** a zavřete dialogové okno.  
  
## <a name="example"></a>Příklad  
 Následující kód zkopíruje `sourcePath` adresář, který určuje `destinationPath` do adresáře, který určuje. Tento kód také poskytuje standardní dialogové okno, které zobrazuje odhadované množství času zbývajícího před dokončením operace.  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a>Viz také

- [Systém souborů a registr (Průvodce programováním v C#)](./index.md)
