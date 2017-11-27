---
title: "RemoveHandler – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 82d130c6536df7d72977a028333293b4e0ee89de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [AddHandler – příkaz](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [Obslužné rutiny](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
