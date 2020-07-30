---
title: Postup poskytnutí dialogového okna průběhu pro Souborová operace – Průvodce programováním v C#
description: Naučte se, jak poskytnout dialogové okno průběhu pro operace se soubory pomocí metody CopyFile (String, String, UIOption).
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 2ea18d924b47fc10412d37479f1b09f7eef7ad3b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301967"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>Postup poskytnutí dialogového okna průběhu pro operace se soubory (Průvodce programováním v C#)
Můžete zadat standardní dialogové okno, které zobrazí průběh operací se soubory ve Windows, pokud použijete <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> metodu v <xref:Microsoft.VisualBasic?displayProperty=nameWithType> oboru názvů.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a>Přidání odkazu v aplikaci Visual Studio  
  
1. V panelu nabídek vyberte položku **projekt**, **Přidat odkaz**.  
  
     Zobrazí se dialogové okno **Správce odkazů** .  
  
2. V oblasti **sestavení** vyberte možnost **rozhraní** , pokud již není zvolena.  
  
3. V seznamu názvů zaškrtněte políčko **Microsoft. VisualBasic** a kliknutím na tlačítko **OK** zavřete dialogové okno.  
  
## <a name="example"></a>Příklad  
 Následující kód zkopíruje adresář, který `sourcePath` Určuje do adresáře, který `destinationPath` Určuje. Tento kód také obsahuje standardní dialogové okno, ve kterém se zobrazuje odhadované množství času zbývajícího před dokončením operace.  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a>Viz také:

- [Systém souborů a registr (Průvodce programováním v C#)](./index.md)
