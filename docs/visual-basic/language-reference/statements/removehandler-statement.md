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
ms.openlocfilehash: 3514a79f2430b148e6a3727b83029b4e207a677b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404249"
---
# <a name="removehandler-statement"></a>RemoveHandler – příkaz
Odebere přidružení mezi událostí a obslužnou rutinou události.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Součásti  
  
|Pojem|Definice|  
|---|---|  
|`event`|Název zpracovávané události.|  
|`eventhandler`|Název procedury, která tuto událost právě zpracovává.|  
  
## <a name="remarks"></a>Poznámky  
 `AddHandler`Příkazy a `RemoveHandler` umožňují kdykoli během provádění programu spouštět a zastavovat zpracování událostí pro konkrétní událost.  
  
> [!NOTE]
> Pro vlastní události `RemoveHandler` Vyvolá příkaz přístup k události `RemoveHandler` . Další informace o vlastních událostech naleznete v tématu [příkaz Event](event-statement.md).  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Viz také

- [AddHandler – příkaz](addhandler-statement.md)
- [Handles](handles-clause.md)
- [Event – příkaz](event-statement.md)
- [Události](../../programming-guide/language-features/events/index.md)
