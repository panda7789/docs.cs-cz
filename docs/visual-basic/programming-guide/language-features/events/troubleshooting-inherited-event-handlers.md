---
title: Řešení potíží s obslužnými rutinami zděděných událostí
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: 4e7bedd1de5197fcf8b69091f4cc878f41b01cd5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405103"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic
V tomto tématu jsou uvedeny běžné problémy, které vznikají pomocí obslužných rutin událostí ve zděděných součástech.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>Kód v obslužné rutině události se spustí dvakrát pro každé volání.  
  
- Zděděná obslužná rutina události nesmí obsahovat klauzuli [Handles](../../../language-reference/statements/handles-clause.md) . Metoda v základní třídě je již k události přidružena a bude ji následně zavolávat. Odeberte `Handles` klauzuli z zděděné metody.  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- Pokud zděděná metoda neobsahuje `Handles` klíčové slovo, ověřte, že váš kód neobsahuje další [příkaz AddHandler](../../../language-reference/statements/addhandler-statement.md) , ani žádné další metody, které zpracovávají stejnou událost.  
  
## <a name="see-also"></a>Viz také

- [Události](index.md)
