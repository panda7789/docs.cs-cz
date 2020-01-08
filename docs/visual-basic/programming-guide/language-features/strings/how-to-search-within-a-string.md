---
title: 'Postupy: vyhledávání v řetězci'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: 655f746e4e496e1935afcd2a9f9fe36d9e3a2564
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348425"
---
# <a name="how-to-search-within-a-string-visual-basic"></a>Postupy: vyhledávání v řetězci (Visual Basic)

Tento článek ukazuje příklad, jak hledat v řetězci v Visual Basic.

## <a name="example"></a>Příklad

V tomto příkladu je volána metoda <xref:System.String.IndexOf%2A> na objektu <xref:System.String>, aby se nahlásil index prvního výskytu podřetězce:

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a>Robustní programování

Metoda <xref:System.String.IndexOf%2A> vrací umístění prvního znaku prvního výskytu podřetězce. Index je založen na 0, což znamená, že první znak řetězce má index 0.

Pokud <xref:System.String.IndexOf%2A> nenajde dílčí řetězec, vrátí-1.

Metoda <xref:System.String.IndexOf%2A> rozlišuje velká a malá písmena a používá aktuální jazykovou verzi.

Pro zajištění optimálního řízení chyb může být vhodné uzavřít hledání řetězce v `Try` bloku [Try... Zachytit... Finally](../../../language-reference/statements/try-catch-finally-statement.md) – konstrukce příkazu.

## <a name="see-also"></a>Viz také:

- <xref:System.String.IndexOf%2A>
- [Příkaz Try...Catch...Finally](../../../language-reference/statements/try-catch-finally-statement.md)
- [Seznámení s řetězci v Visual Basic](introduction-to-strings.md)
- [Řetězce](index.md)
