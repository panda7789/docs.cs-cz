---
title: 'Postup: Otevření souborů pomocí komponenty OpenFileDialog'
ms.date: 02/11/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: ca69de19ab1b9ae387002898145fe99e35a7b6b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182135"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a>Postup: Otevření souborů pomocí dialogu OpenFileDialog

Komponenta <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> otevře dialogové okno Systému Windows pro procházení a výběr souborů. Chcete-li otevřít a číst vybrané <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> soubory, můžete použít metodu nebo vytvořit instanci třídy. <xref:System.IO.StreamReader?displayProperty=nameWithType> Následující příklady ukazují oba přístupy.

V rozhraní .NET Framework vyžaduje <xref:System.Windows.Forms.FileDialog.FileName%2A> získání nebo nastavení vlastnosti úroveň oprávnění udělenou třídou. <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> Příklady spustit <xref:System.Security.Permissions.FileIOPermission> kontrolu oprávnění a může vyvolat výjimku z důvodu nedostatečných oprávnění, pokud jsou spuštěny v kontextu částečné důvěryhodnosti. Další informace naleznete v [tématu Základy zabezpečení přístupu kódu](../../misc/code-access-security-basics.md).

Tyto příklady můžete vytvořit a spustit jako aplikace rozhraní .NET Framework z příkazového řádku jazyka C# nebo Visual Basic. Další informace naleznete v [tématu Vytváření příkazového řádku s csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) nebo [Sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

Počínaje rozhraním .NET Core 3.0 můžete také vytvářet a spouštět příklady jako aplikace Windows .NET Core ze složky, která má název složky .NET Core Windows Forms * \<>.csproj* soubor projektu.

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a>Příklad: Čtení souboru jako datového proudu pomocí streamreaderu  
  
Následující příklad používá obslužnou rutinu <xref:System.Windows.Forms.OpenFileDialog> události <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> ovládacího <xref:System.Windows.Forms.Control.Click> prvku Windows Forms <xref:System.Windows.Forms.Button> k otevření metody s. Poté, co uživatel vybere soubor **OK**a vybere OK <xref:System.IO.StreamReader> , instance třídy přečte soubor a zobrazí jeho obsah v textovém poli formuláře. Další informace o čtení z datových proudů souborů naleznete v tématu <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> a <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a>Příklad: Otevření souboru z filtrovaného výběru pomocí openfile

Následující příklad používá <xref:System.Windows.Forms.Button> obslužnou rutinu události ovládacího <xref:System.Windows.Forms.Control.Click> prvku k otevření <xref:System.Windows.Forms.OpenFileDialog> filtru, který zobrazuje pouze textové soubory. Poté, co uživatel vybere textový **OK**soubor a <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> vybere OK , metoda se používá k otevření souboru v poznámkovém bloku.

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.OpenFileDialog>
- [Komponenta OpenFileDialog](openfiledialog-component-windows-forms.md)
