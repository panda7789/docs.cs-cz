---
title: 'Postupy: vyhledávání v řetězci Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: fe9e50dc5458fdf8546094e5f41c2f001f1d2791
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700065"
---
# <a name="how-to-search-within-a-string-visual-basic"></a>Postupy: vyhledávání v řetězci (Visual Basic)

Tento článek ukazuje příklad, jak hledat v řetězci v Visual Basic.

## <a name="example"></a>Příklad

Tento příklad volá metodu <xref:System.String.IndexOf%2A> u objektu <xref:System.String>, aby nahlásila index prvního výskytu podřetězce:

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a>Robustní programování

Metoda <xref:System.String.IndexOf%2A> vrací umístění prvního znaku prvního výskytu podřetězce. Index je založen na 0, což znamená, že první znak řetězce má index 0.

Pokud <xref:System.String.IndexOf%2A> nenajde podřetězec, vrátí-1.

Metoda <xref:System.String.IndexOf%2A> rozlišuje velká a malá písmena a používá aktuální jazykovou verzi.

Pro zajištění optimálního řízení chyb může být vhodné uzavřít hledání řetězce v bloku `Try` příkazu [Try... Zachytit... Finally](../../../language-reference/statements/try-catch-finally-statement.md) – konstrukce příkazu.

## <a name="see-also"></a>Viz také:

- <xref:System.String.IndexOf%2A>
- [Příkaz Try...Catch...Finally](../../../language-reference/statements/try-catch-finally-statement.md)
- [Seznámení s řetězci v Visual Basic](introduction-to-strings.md)
- [Řetězce](index.md)
