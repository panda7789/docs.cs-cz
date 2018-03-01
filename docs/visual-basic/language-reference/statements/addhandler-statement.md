---
title: "AddHandler – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07fbfe04ccd01b7d0f99338ef2682238830099dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="addhandler-statement"></a>AddHandler – příkaz
Přidruží událost obslužné rutiny události za běhu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Součásti  
 `event`  
 Název události ke zpracování.  
  
 `eventhandler`  
 Název procedury, která zpracovává událost.  
  
## <a name="remarks"></a>Poznámky  
 `AddHandler` a `RemoveHandler` příkazy umožňují spuštění a zastavení zpracování událostí v průběhu provádění programu.  
  
 Podpis `eventhandler` postupu musí odpovídat podpis události `event`.  
  
 `Handles` – Klíčové slovo a `AddHandler` příkaz oba umožňují určit, že konkrétní postupy zpracování konkrétní události, ale jsou rozdíly. `AddHandler` Příkaz připojí postupy pro události za běhu. Použití `Handles` – klíčové slovo při definování postup, chcete-li určit, která byla zjištěna určitá událost. Další informace najdete v tématu [zpracovává](../../../visual-basic/language-reference/statements/handles-clause.md).  
  
> [!NOTE]
>  Pro vlastní události `AddHandler` příkaz volá události `AddHandler` přistupujícího objektu. Další informace o vlastních událostí najdete v tématu [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [RemoveHandler – příkaz](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [Obslužné rutiny](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
