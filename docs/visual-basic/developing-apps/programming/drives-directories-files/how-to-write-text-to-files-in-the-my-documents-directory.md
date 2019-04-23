---
title: 'Postupy: Zápis textu do souborů adresáři MyDocuments v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: 4f9eb4c9e0eb92712b5ea1a4feef24f2bb95d70b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973775"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a>Postupy: Zápis textu do souborů adresáři MyDocuments v jazyce Visual Basic
`My.Computer.FileSystem.SpecialDirectories` Objekt umožňuje přístup k adresářům speciální, například **MyDocuments** adresáře.  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a>Psaní nové textové soubory v adresáři Moje dokumenty  
  
1. Použití `My.Computer.FileSystem.SpecialDirectories.MyDocuments` vlastnost zadat cestu.  
  
     [!code-vb[VbFileIOWrite#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#1)]  
  
2. Použití `WriteAllText` způsob zápisu textu do zadaného souboru.  
  
     [!code-vb[VbVbcnMyFileSystem#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#14)]  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbFileIOWrite#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Nahraďte `test.txt` s názvem souboru chcete zapsat.  
  
## <a name="robust-programming"></a>Robustní programování  
 Tento kód znovu vyvolá všechny výjimky, které mohou nastat při zápisu textu do souboru. Snížíte pravděpodobnost, že výjimky pomocí ovládacích prvků Windows Forms, jako [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) a [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) součásti, které omezují výběr uživatele na platný název souboru. Pomocí těchto ovládacích prvků není spolehlivá, ale. Systém souborů můžete změnit mezi časem uživatel vybere soubor a čas, který spouští kód. Zpracování výjimek je proto téměř vždy nezbytné při práci se soubory.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Pokud používáte v kontextu částečným vztahem důvěryhodnosti, kód může vyvolat výjimku, protože nedostatečná oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).  
  
 Tento příklad vytvoří nový soubor. Pokud aplikace potřebuje vytvořit soubor, tato aplikace potřebuje vytvořit oprávnění pro složku. Oprávnění se nastavují pomocí seznamů řízení přístupu. Pokud soubor již existuje, aplikace potřebuje pouze oprávnění, a menší oprávnění k zápisu. Kde je to možné, je bezpečnější vytvořit soubor při nasazení a udělit pouze oprávnění ke čtení pro jeden soubor, nikoli k udělení oprávnění vytvořit pro složku. Navíc je bezpečnější zapsat data do uživatelské složky než do kořenové složky nebo **Program Files** složky. Další informace najdete v tématu [Přehled technologie ACL](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
