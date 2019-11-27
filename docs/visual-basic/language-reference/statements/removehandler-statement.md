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
ms.openlocfilehash: 177952acf362ccb36a36b5f09b11a1a93dbefa29
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333041"
---
# <a name="removehandler-statement"></a>RemoveHandler – příkaz
Odebere přidružení mezi událostí a obslužnou rutinou události.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`event`|Název zpracovávané události.|  
|`eventhandler`|Název procedury, která tuto událost právě zpracovává.|  
  
## <a name="remarks"></a>Poznámky  
 Příkazy `AddHandler` a `RemoveHandler` umožňují kdykoli během provádění programu spouštět a zastavovat zpracování událostí pro konkrétní událost.  
  
> [!NOTE]
> Pro vlastní události příkaz `RemoveHandler` vyvolá přistupující objekt `RemoveHandler` události. Další informace o vlastních událostech naleznete v tématu [příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [Řeší](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
