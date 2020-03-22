---
title: 'Postupy: Zápis textu do souborů v adresáři MyDocuments'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: bc62f2bc63a2ea185b8ea4c8d271dd28d347d6f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334524"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a>Postupy: Zápis textu do souborů v adresáři MyDocuments v jazyce Visual Basic

Objekt `My.Computer.FileSystem.SpecialDirectories` umožňuje přístup ke speciálním adresářům, například adresáři **MyDocuments.**  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a>Zápis nových textových souborů do adresáře Dokumenty  
  
1. Pomocí `My.Computer.FileSystem.SpecialDirectories.MyDocuments` vlastnosti dodejte cestu.  
  
     [!code-vb[VbFileIOWrite#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#1)]  
  
2. Pomocí `WriteAllText` metody zapište text do zadaného souboru.  
  
     [!code-vb[VbVbcnMyFileSystem#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#14)]  
  
## <a name="example"></a>Příklad  

 [!code-vb[VbFileIOWrite#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  

 Nahraďte `test.txt` název souboru, do kterého chcete zapisovat.  
  
## <a name="robust-programming"></a>Robustní programování  

 Tento kód znovu vyvolá všechny výjimky, které mohou nastat při zápisu textu do souboru. Pravděpodobnost výjimek můžete snížit pomocí ovládacích prvků windows forms, jako jsou komponenty [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) a [SaveFileDialog,](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) které omezují volby uživatelů na platné názvy souborů. Použití těchto ovládacích prvků však není spolehlivé. Systém souborů může měnit mezi časem, kdy uživatel vybere soubor, a časem, kdy se kód spustí. Zpracování výjimek je proto téměř vždy nutné při práci se soubory.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  

 Pokud jsou spuštěny v kontextu částečné důvěryhodnosti, kód může vyvolat výjimku z důvodu nedostatečných oprávnění. Další informace naleznete v [tématu Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).  
  
 Tento příklad vytvoří nový soubor. Pokud aplikace potřebuje vytvořit soubor, tato aplikace potřebuje vytvořit oprávnění pro složku. Oprávnění jsou nastavena pomocí seznamů řízení přístupu. Pokud soubor již existuje, aplikace potřebuje pouze oprávnění k zápisu, menší oprávnění. Pokud je to možné, je bezpečnější vytvořit soubor během nasazení a udělit oprávnění pro čtení pouze jeden soubor, spíše než udělit oprávnění vytvořit pro složku. Také je bezpečnější zapisovat data do uživatelských složek než do kořenové složky nebo do složky **Program Files.** Další informace naleznete v tématu [Přehled technologie ACL](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
