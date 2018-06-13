---
title: RemoveHandler – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 0d982768707948bd6c616445509e16a462b86f2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597985"
---
# <a name="removehandler-statement"></a>RemoveHandler – příkaz
Odebere přidružení mezi událost a obslužné rutiny události.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`event`|Název události ke zpracování.|  
|`eventhandler`|Název procesu, který aktuálně zpracovává událost.|  
  
## <a name="remarks"></a>Poznámky  
 `AddHandler` a `RemoveHandler` příkazy umožňují spuštění a zastavení zpracování událostí pro určitou událost kdykoli během spuštění programu.  
  
> [!NOTE]
>  Pro vlastní události `RemoveHandler` příkaz volá události `RemoveHandler` přistupujícího objektu. Další informace o vlastních událostí najdete v tématu [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Příkaz AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [Obslužné rutiny](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
