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
ms.openlocfilehash: 5650298da99f8bc9a25c7d7ceea11a8a5bf968fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587523"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a>Řešení potíží: čtení a zápis do textových souborů (Visual Basic)
Toto téma popisuje běžné problémy při práci s textem soubory a navrhne jejich řešení.  
  
## <a name="common-problems"></a>Běžné problémy  
 Většina běžných potíží při práci s textovými soubory zahrnovat výjimky zabezpečení, kódování souborů nebo neplatné cesty.  
  
### <a name="security-exceptions"></a>Výjimky zabezpečení  
 A <xref:System.Security.SecurityException> se vyvolá, když dojde k chybě zabezpečení. Toto je často výsledek nedostatečných oprávnění, což může být vyřešen přidáním oprávnění nebo práce se soubory v izolovaném úložišti uživatele.  
  
### <a name="file-encodings"></a>Kódování souborů  
 Kódování souborů, také známé jako kódování znaků, určete, jak představují znaky při zpracování textu. Neočekávané znaků v textovém souboru může být důsledkem nesprávné kódování. Většina souborů jeden kódování může být vhodnější než oproti jinému z hlediska jazykové symboly může nebo nemůže zpracovat, i když je obvykle upřednostňované kódování Unicode. Další informace najdete v tématu [kódování souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) a <xref:System.Text.Encoding>.  
  
### <a name="incorrect-paths"></a>Nesprávné cesty  
 Při analýze cesty k souborům, zejména relativní cesty, je snadné k poskytování chybná data. Mnoho problémů může být vyřešen tím, že zajistí, že zadáváte správnou cestu. Další informace najdete v tématu [postupy: Analýza cest k souborům](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 [Čtení ze souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [Zápis do souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 [Analýza textových souborů pomocí objektu TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
