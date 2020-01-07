---
title: Postup poskytnutí dialogového okna průběhu pro Souborová operace – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: bec718660b998c6d29fe014abffef1bae705deb0
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635636"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>Postup poskytnutí dialogového okna průběhu pro operace se soubory (C# Průvodce programováním)
Můžete zadat standardní dialogové okno, které zobrazí průběh operací se soubory ve Windows, pokud použijete metodu <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> v oboru názvů <xref:Microsoft.VisualBasic?displayProperty=nameWithType>.  
  
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
