---
title: Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: 704ca667a6d14ade7be0192e872f5e40791cb864
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58830185"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic
Toto téma obsahuje seznam běžných problémů, které vznikají u obslužných rutin událostí v zděděné součásti.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>Spustí kód v obslužné rutině události dvakrát za každé volání  
  
-   Nesmí obsahovat obslužnou rutinu zděděné události [zpracovává](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli. Metodu v základní třídě je již přidruženo k události a odpovídajícím způsobem se aktivuje. Odeberte `Handles` klauzule z zděděné metody.  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
-   Pokud nemá žádné zděděné metody `Handles` – klíčové slovo, ověřte, že váš kód neobsahuje speciální [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md) nebo jakékoli další metody, které zpracovávají stejné události.  
  
## <a name="see-also"></a>Viz také:

- [Události](../../../../visual-basic/programming-guide/language-features/events/index.md)
