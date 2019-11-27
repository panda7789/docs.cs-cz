---
title: Kódování souborů
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: 52770187568d0ba0f54ec36ee2c3d754a9b4d9a8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348882"
---
# <a name="file-encodings-visual-basic"></a>Kódování souborů (Visual Basic)

Kódování souborů, označovaná také jako kódování znaků, určují způsob reprezentace znaků při zpracování textu. Jedno kódování může být vhodnější než jiné, a to z toho smyslu, které znaky jazyka může nebo nemůže zpracovat, i když je obvykle upřednostňovaný Unicode.

Při čtení nebo zapisování do souborů může nesprávně odpovídat kódování souborů způsobit výjimky nebo nesprávné výsledky.

## <a name="types-of-encodings"></a>Typy kódování

Unicode je preferované kódování při práci se soubory. Unicode je celosvětový standard kódování znaků, který používá 16bitové hodnoty kódu pro reprezentaci všech znaků používaných v moderních výpočetních prostředích, včetně technických symbolů a speciálních znaků používaných při publikování.

Předchozí standardy kódování znaků se skládají z tradičních znakových sad, jako je například znaková sada Windows ANSI, která používá 8bitové hodnoty kódu, nebo kombinace 8 bitových hodnot, které reprezentují znaky používané v konkrétním jazyce nebo geografické oblasti.

## <a name="encoding-class"></a>Encoding – třída

Třída <xref:System.Text.Encoding> představuje kódování znaků. Tato tabulka uvádí typy dostupných kódování a popisuje je.

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
