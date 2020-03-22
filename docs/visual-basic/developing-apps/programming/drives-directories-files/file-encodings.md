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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348882"
---
# <a name="file-encodings-visual-basic"></a>Kódování souborů (Visual Basic)

Kódování souborů, označované také jako kódování znaků, určují, jak mají při zpracování textu představovat znaky. Jedno kódování může být vhodnější než jiné, pokud jde o jazyk, který může nebo nemůže zpracovat, ačkoli Unicode je obvykle upřednostňován.

Při čtení nebo zápisu do souborů může mít nesprávně odpovídající kódování souborů za následek výjimky nebo nesprávné výsledky.

## <a name="types-of-encodings"></a>Typy kódování

Unicode je upřednostňované kódování při práci se soubory. Unicode je celosvětový standard kódování znaků, který používá 16bitové kódové hodnoty k reprezentaci všech znaků používaných v moderním výpočetním prostředí, včetně technických symbolů a speciálních znaků používaných při publikování.

Předchozí standardy kódování znaků se skládaly z tradičních znakových sad, jako je například znaková sada Systému Windows ANSI, která používá 8bitové kódové hodnoty nebo kombinace 8bitových hodnot k reprezentaci znaků používaných v určitém jazyce nebo zeměpisné oblasti.

## <a name="encoding-class"></a>Třída kódování

Třída <xref:System.Text.Encoding> představuje kódování znaků. V této tabulce je uveden typ kódování, která jsou k dispozici, a popisuje každé kódování.

|Name (Název)|Popis|
|---|---|
|<xref:System.Text.ASCIIEncoding>|Představuje znak ASCII kódování znaků Unicode.|
|<xref:System.Text.UnicodeEncoding>|Představuje kódování UTF-16 znaků Unicode.|
|<xref:System.Text.UTF32Encoding>|Představuje kódování UTF-32 znaků Unicode.|
|<xref:System.Text.UTF7Encoding>|Představuje kódování UTF-7 znaků Unicode.|
|<xref:System.Text.UTF8Encoding>|Představuje kódování UTF-8 znaků Unicode.|

## <a name="see-also"></a>Viz také

- [Čtení ze souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Zápis do souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
