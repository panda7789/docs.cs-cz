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

Objekt umožňuje přístup ke speciálním adresářům, jako je například adresář **dokumenty.** `My.Computer.FileSystem.SpecialDirectories`  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a>Zápis nových textových souborů do adresáře My Documents  
  
1. K poskytnutí `My.Computer.FileSystem.SpecialDirectories.MyDocuments` cesty použijte vlastnost.  
  
     [!code-vb[VbFileIOWrite#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#1)]  
  
2. Použijte `WriteAllText` metodu k zápisu textu do zadaného souboru.  
  
     [!code-vb[VbVbcnMyFileSystem#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#14)]  
  
## <a name="example"></a>Příklad  

 [!code-vb[VbFileIOWrite#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  

 Nahraďte `test.txt` názvem souboru, do kterého chcete zapisovat.  
  
## <a name="robust-programming"></a>Robustní programování  

 Tento kód znovu vyvolá všechny výjimky, které mohou nastat při zápisu textu do souboru. Můžete snížit pravděpodobnost výjimek pomocí model Windows Forms ovládací prvky, jako jsou například [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) a komponenty [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) , které omezují možnosti uživatele na platné názvy souborů. Použití těchto ovládacích prvků není však foolproof. Systém souborů se může změnit mezi časem, kdy uživatel vybere soubor a čas, kdy se kód spustí. Zpracování výjimek je proto skoro vždy nutné při práci se soubory.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  

 Pokud používáte v kontextu s částečným vztahem důvěryhodnosti, může kód vyvolat výjimku z důvodu nedostatečných oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../../../framework/misc/code-access-security-basics.md).  
  
 Tento příklad vytvoří nový soubor. Pokud aplikace potřebuje vytvořit soubor, potřebuje tato aplikace oprávnění vytvořit pro tuto složku. Oprávnění se nastavují pomocí seznamů řízení přístupu. Pokud soubor již existuje, aplikace potřebuje pouze oprávnění Write, což je menší oprávnění. Pokud je to možné, je bezpečnější vytvořit soubor během nasazení a udělit pouze oprávnění ke čtení pro jeden soubor místo udělení oprávnění k vytvoření složky. Je také bezpečnější zapsat data do složek uživatele než do kořenové složky nebo do složky **Program Files** . Další informace najdete v tématu [Přehled technologie ACL](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
