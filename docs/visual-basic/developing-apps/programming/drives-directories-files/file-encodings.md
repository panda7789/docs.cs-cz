---
title: Kódování souborů (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: d73226c58d39c970ec02c32a2c188f2747a7d87e
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583467"
---
# <a name="file-encodings-visual-basic"></a>Kódování souborů (Visual Basic)

Kódování souborů, označovaná také jako kódování znaků, určují způsob reprezentace znaků při zpracování textu. Jedno kódování může být vhodnější než jiné, a to z toho smyslu, které znaky jazyka může nebo nemůže zpracovat, i když je obvykle upřednostňovaný Unicode.

Při čtení nebo zapisování do souborů může nesprávně odpovídat kódování souborů způsobit výjimky nebo nesprávné výsledky.

## <a name="types-of-encodings"></a>Typy kódování

Unicode je preferované kódování při práci se soubory. Unicode je celosvětový standard kódování znaků, který používá 16bitové hodnoty kódu pro reprezentaci všech znaků používaných v moderních výpočetních prostředích, včetně technických symbolů a speciálních znaků používaných při publikování.

Předchozí standardy kódování znaků se skládají z tradičních znakových sad, jako je například znaková sada Windows ANSI, která používá 8bitové hodnoty kódu, nebo kombinace 8 bitových hodnot, které reprezentují znaky používané v konkrétním jazyce nebo geografické oblasti.

## <a name="encoding-class"></a>Encoding – třída

Třída <xref:System.Text.Encoding> představuje kódování znaků. Tato tabulka uvádí typy dostupných kódování a popisuje je.

|Name|Popis|
|---|---|
|<xref:System.Text.ASCIIEncoding>|Představuje kódování znaků ASCII znaků Unicode.|
|<xref:System.Text.UnicodeEncoding>|Představuje kódování UTF-16 znaků Unicode.|
|<xref:System.Text.UTF32Encoding>|Představuje kódování UTF-32 znaků Unicode.|
|<xref:System.Text.UTF7Encoding>|Představuje kódování UTF-7 znaků Unicode.|
|<xref:System.Text.UTF8Encoding>|Představuje kódování UTF-8 znaků Unicode.|

## <a name="see-also"></a>Viz také:

- [Čtení ze souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Zápis do souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
