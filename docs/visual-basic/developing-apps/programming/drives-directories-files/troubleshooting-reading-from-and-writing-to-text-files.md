---
title: 'Řešení potíží: čtení z textových souborů a zápis do nich'
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
ms.openlocfilehash: 8af4160d09f39f2622a007aef793173d614a8b44
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406622"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a>Řešení potíží: čtení z textových souborů a zápis do nich (Visual Basic)

Toto téma popisuje běžné problémy zjištěné při práci s textovými soubory a navrhuje přístup k jednotlivým.  
  
## <a name="common-problems"></a>Běžné problémy  

 Nejběžnější problémy, ke kterým došlo při práci s textovými soubory, zahrnují výjimky zabezpečení, kódování souborů nebo neplatné cesty.  
  
### <a name="security-exceptions"></a>Výjimky zabezpečení  

 <xref:System.Security.SecurityException>Výjimka je vyvolána, když dojde k chybě zabezpečení. To často vede k tomu, že uživatel nemá potřebná oprávnění, která se můžou vyřešit přidáváním oprávnění nebo práci se soubory v izolovaném úložišti.  
  
### <a name="file-encodings"></a>Kódování souborů  

 Kódování souborů, označovaná také jako kódování znaků, určují způsob reprezentace znaků při zpracování textu. Neočekávané znaky v textovém souboru mohou být způsobeny nesprávným kódováním. U většiny souborů může být jedno kódování vhodnější než jiné z důvodu toho, které znaky jazyka může nebo nemůže zpracovat, i když je standardu Unicode obvykle upřednostňovaný. Další informace naleznete v tématu [kódování souborů](file-encodings.md) a <xref:System.Text.Encoding> .  
  
### <a name="incorrect-paths"></a>Nesprávné cesty  

 Při analýze cest k souborům, zejména relativních cest, je snadné zadávat nesprávná data. Mnohé problémy se dají opravit tím, že zadáte správnou cestu. Další informace najdete v tématu [Postup: analýza cest k souborům](how-to-parse-file-paths.md).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [Čtení ze souborů](reading-from-files.md)
- [Zápis do souborů](writing-to-files.md)
- [Analýza textových souborů pomocí objektu TextFieldParser](parsing-text-files-with-the-textfieldparser-object.md)
