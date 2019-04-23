---
title: 'Postupy: Otevírání souborů pomocí komponenty OpenFileDialog'
ms.date: 02/11/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: 7f4e96f1714a182647665f12e29d38f2b8037478
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159104"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a>Postupy: Otevřít soubory s OpenFileDialog 

<xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> Komponenty otevře dialogové okno Windows pro procházení a výběr souborů. Otevřít a přečíst si vybrané soubory, můžete použít <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> metodu, nebo vytvořit instanci <xref:System.IO.StreamReader?displayProperty=nameWithType> třídy. Následující příklady ukazují oba přístupy. 

V rozhraní .NET Framework pro získání nebo nastavení <xref:System.Windows.Forms.FileDialog.FileName%2A> vlastnost vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> třídy. Spuštění příkladů <xref:System.Security.Permissions.FileIOPermission> oprávnění Zkontrolujte a může vyvolat výjimku z důvodu nedostatečné oprávnění, pokud spuštění v kontextu částečným vztahem důvěryhodnosti. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../misc/code-access-security-basics.md).

Můžete sestavit a spustit tyto příklady jako aplikace rozhraní .NET Framework C# nebo příkazového řádku jazyka Visual Basic. Další informace najdete v tématu [příkazového řádku pomocí csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) nebo [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md). 

Od verze .NET Core 3.0, můžete také sestavit a spustit v příkladech jako Windows aplikace .NET Core ze složky, která má formulářů Windows .NET Core  *\<název složky > .csproj* souboru projektu. 

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a>Příklad: Čtení souboru jako datový proud pomocí třídy StreamReader  
  
Následující příklad používá Windows Forms <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> obslužná rutina události otevřete <xref:System.Windows.Forms.OpenFileDialog> s <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody. Poté, co uživatel vybere soubor a vybere **OK**, instance <xref:System.IO.StreamReader> třídy načte soubor a zobrazí jeho obsah v textovém poli formuláři. Další informace o čtení ze souborů datových proudů, naleznete v tématu <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> a <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a>Příklad: Otevřete soubor z filtrovaný výběr s OpenFile 

V následujícím příkladu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> obslužná rutina události otevřete <xref:System.Windows.Forms.OpenFileDialog> s filtrem, který zobrazuje pouze textové soubory. Poté, co uživatel vybere textový soubor a vybere **OK**, <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda se používá k otevření souboru v poznámkovém bloku.

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.OpenFileDialog>
- [OpenFileDialog – komponenta](openfiledialog-component-windows-forms.md)
