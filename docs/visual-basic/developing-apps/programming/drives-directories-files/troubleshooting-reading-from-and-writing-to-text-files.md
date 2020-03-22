---
title: 'Řešení potíží: čtení a zápis do textových souborů'
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
ms.openlocfilehash: dbc53ca3cc9ae9b2d14b925f891d0409b2b7debd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333789"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a>Řešení potíží: čtení a zápis do textových souborů (Visual Basic)

Toto téma popisuje běžné problémy při práci s textovými soubory a navrhuje přístup ke každému z nich.  
  
## <a name="common-problems"></a>Běžné problémy  

 Mezi nejčastější problémy při práci s textovými soubory patří výjimky zabezpečení, kódování souborů nebo neplatné cesty.  
  
### <a name="security-exceptions"></a>Výjimky zabezpečení  

 A <xref:System.Security.SecurityException> je vyvolána, když dojde k chybě zabezpečení. To je často důsledkem toho, že uživatel i min. nemá potřebná oprávnění, která mohou být vyřešena přidáním oprávnění nebo prací se soubory v izolovaném úložišti.  
  
### <a name="file-encodings"></a>Kódování souborů  

 Kódování souborů, označované také jako kódování znaků, určují, jak mají při zpracování textu představovat znaky. Neočekávané znaky v textovém souboru mohou být důsledkem nesprávného kódování. U většiny souborů může být jedno kódování vhodnější než jiné, pokud jde o znaky jazyka, které může nebo nemůže zpracovat, ačkoli unicode je obvykle upřednostňováno. Další informace naleznete v [tématu Kódování souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) a <xref:System.Text.Encoding>.  
  
### <a name="incorrect-paths"></a>Nesprávné cesty  

 Při analýzě cest souboru, zejména relativní cesty, je snadné zadat nesprávná data. Mnoho problémů lze opravit tím, že se ujistíte, že poskytujete správnou cestu. Další informace naleznete v [tématu How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [Čtení ze souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Zápis do souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [Analýza textových souborů pomocí objektu TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
