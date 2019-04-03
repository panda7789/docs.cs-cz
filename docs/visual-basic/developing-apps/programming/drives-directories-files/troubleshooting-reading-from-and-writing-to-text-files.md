---
title: 'Řešení potíží: čtení a zápis do textových souborů (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
ms.openlocfilehash: 90a04d9de2ac77c28a92d99e1fe118a1f8ecf448
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831776"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a>Řešení potíží: čtení a zápis do textových souborů (Visual Basic)
Toto téma popisuje běžné problémy vzniklé při práci s textem soubory a navrhne přístup ke každému.  
  
## <a name="common-problems"></a>Běžné problémy  
 Nejběžnějších problémů při práci s textovými soubory zahrnují bezpečnostním výjimkám, kódování souborů nebo neplatné cesty.  
  
### <a name="security-exceptions"></a>Výjimky zabezpečení  
 A <xref:System.Security.SecurityException> je vyvolána, když dojde k chybě zabezpečení. To je často důsledkem nedostatečných oprávnění, která může vyřešit přidáním oprávnění nebo práce se soubory v izolovaném úložišti uživatele.  
  
### <a name="file-encodings"></a>Kódování souborů  
 Kódování souborů, označované také jako kódování znaků, určete, jak reprezentaci znaků při zpracování textu. Z nesprávné kódování může způsobit neočekávané znaky do textového souboru. Pro většinu souborů kódování může být vhodnější před jiným z hlediska znaků jazyka může nebo nemůže zpracovat, i když je obvykle ve formátu Unicode. Další informace najdete v tématu [kódování souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) a <xref:System.Text.Encoding>.  
  
### <a name="incorrect-paths"></a>Nesprávné cesty  
 Při analýze cesty k souborům, zejména relativní cesty, je snadné slouží k poskytování chybná data. Mnoho problémů může být vyřešen a ujistěte se, že zadáváte správnou cestu. Další informace najdete v tématu [jak: Analýza cest k souborům](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [Čtení ze souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Zápis do souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [Analýza textových souborů pomocí objektu TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
