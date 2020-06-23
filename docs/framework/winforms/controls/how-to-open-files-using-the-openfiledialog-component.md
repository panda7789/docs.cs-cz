---
title: 'Postupy: otevření souborů pomocí komponenty OpenFileDialog'
ms.date: 02/11/2019
description: Naučte se používat komponentu OpenFileDialog k otevření dialogového okna Windows pro procházení a výběr souborů.
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: d571885011b0f0c723c73a417f294f30f96952f4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904426"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a>Postupy: otevření souborů pomocí OpenFileDialog

<xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType>Komponenta otevře dialogové okno Windows pro procházení a výběr souborů. Chcete-li otevřít a číst vybrané soubory, můžete použít <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> metodu nebo vytvořit instanci <xref:System.IO.StreamReader?displayProperty=nameWithType> třídy. Následující příklady znázorňují oba přístupy.

V .NET Framework pro získání nebo nastavení <xref:System.Windows.Forms.FileDialog.FileName%2A> vlastnosti vyžaduje úroveň oprávnění udělené <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> třídou. Příklady spouštějí <xref:System.Security.Permissions.FileIOPermission> kontrolu oprávnění a mohou vyvolat výjimku z důvodu nedostatečných oprávnění, pokud jsou spuštěny v kontextu s částečným vztahem důvěryhodnosti. Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../misc/code-access-security-basics.md).

Tyto příklady můžete sestavit a spustit jako aplikace .NET Framework z příkazového řádku jazyka C# nebo Visual Basic. Další informace naleznete v tématu [sestavování z příkazového řádku pomocí csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) nebo [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

Počínaje rozhraním .NET Core 3,0 můžete také sestavit a spustit příklady jako aplikace Windows .NET Core ze složky, která obsahuje soubor projektu .NET Core model Windows Forms * \<folder name> . csproj* .

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a>Příklad: čtení souboru jako datového proudu pomocí StreamReader  
  
V následujícím příkladu je použita <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Click> obslužná rutina události model Windows Forms ovládacího prvku pro otevření <xref:System.Windows.Forms.OpenFileDialog> s <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodou. Poté, co uživatel zvolí soubor a vybere **OK**, instance <xref:System.IO.StreamReader> třídy načte soubor a zobrazí jeho obsah v textovém poli formuláře. Další informace o čtení z datových proudů souborů naleznete v tématu <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> a <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType> .  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a>Příklad: otevření souboru z filtrovaného výběru pomocí OpenFile

Následující příklad používá <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Click> obslužnou rutinu události ovládacího prvku pro otevření <xref:System.Windows.Forms.OpenFileDialog> s filtrem, který zobrazuje pouze textové soubory. Když uživatel zvolí textový soubor a vybere **OK**, <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> použije se k otevření souboru v poznámkovém bloku metoda.

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.OpenFileDialog>
- [OpenFileDialog – komponenta](openfiledialog-component-windows-forms.md)
