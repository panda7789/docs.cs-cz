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
ms.openlocfilehash: 4e53398f97cbd320c0c98250ac5abbc2e4e98027
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981033"
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
