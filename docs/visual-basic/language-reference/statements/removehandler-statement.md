---
title: RemoveHandler – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 8a9dc5874629c1687318496bd7c4016eb318c25a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783930"
---
# <a name="removehandler-statement"></a>RemoveHandler – příkaz
Odebere přidružení mezi událostí a obslužnou rutinu události.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`event`|Název události, kterou bude manipulováno.|  
|`eventhandler`|Název procedury aktuálně zpracovává událost.|  
  
## <a name="remarks"></a>Poznámky  
 `AddHandler` a `RemoveHandler` příkazy umožňují spustit a zastavit zpracování událostí pro určitou událost kdykoli během provádění programu.  
  
> [!NOTE]
>  Pro vlastní události `RemoveHandler` příkaz volá události `RemoveHandler` přistupujícího objektu. Další informace o vlastních událostech najdete v tématu [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [Obslužné rutiny](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
