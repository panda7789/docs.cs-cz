---
title: "Řešení potíží: čtení a zápis do textových souborů (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e836f79cd05dbaa180cc7bf5413ce57004e3500b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
