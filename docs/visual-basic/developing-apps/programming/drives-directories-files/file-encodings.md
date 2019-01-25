---
title: Kódování souborů (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: f7ccd47b8778aa3a374ee102b39038e8df475e9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731917"
---
# <a name="file-encodings-visual-basic"></a>Kódování souborů (Visual Basic)
Kódování souborů, označované také jako kódování znaků, určete, jak reprezentaci znaků při zpracování textu. Kódování může být vhodnější před jiným z hlediska znaků jazyka může nebo nemůže zpracovat, i když je obvykle ve formátu Unicode.  
  
 Při čtení nebo zápis do souborů, nesprávně odpovídající kódování souborů může způsobit výjimky nebo nesprávné výsledky.  
  
## <a name="types-of-encodings"></a>Typy kódování  
 Kódování Unicode je upřednostňovaný kódování při práci se soubory. Kódování Unicode je po celém světě standard kódování znaků, která používá kód 16bitové hodnoty k reprezentaci všech znaků moderní výpočet, včetně technických symbolů a speciální znaky, které se používá při publikování.  
  
 Předchozí standardy kódování znaků se skládal z tradičních znakových sad, jako je například znakovou sadu Windows ANSI, která používá kód 8bitové hodnoty nebo kombinace 8bitové hodnoty k reprezentaci znaků používaných pro konkrétní jazyk nebo geografické oblasti.  
  
## <a name="encoding-class"></a>Kódování třídy  
 <xref:System.Text.Encoding> Třída představuje kódování znaků. Tato tabulka uvádí typ kódování, které jsou k dispozici a popisuje všechny.  
  
|Název|Popis|
|---|---|    
|<xref:System.Text.ASCIIEncoding>|Představuje kódování znaků ASCII znaků Unicode.|  
|<xref:System.Text.UnicodeEncoding>|Představuje kódování UTF-16 znaků Unicode.|  
|<xref:System.Text.UTF32Encoding>|Představuje kódování UTF-32 znaků Unicode.|  
|<xref:System.Text.UTF7Encoding>|Představuje kódování UTF-7 znaků Unicode.|  
|<xref:System.Text.UTF8Encoding>|Představuje kódování UTF-8 znaků Unicode.|  
  
## <a name="see-also"></a>Viz také:
- [Čtení ze souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Zápis do souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
