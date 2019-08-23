---
title: AddHandler – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: a9913cd682e52562422ba140e27187d37c592684
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928941"
---
# <a name="addhandler-statement"></a>AddHandler – příkaz
Přidruží událost k obslužné rutině události v době běhu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Součásti  
|||
|---|---|
|event|Název události, která má být zpracována.|  
|`eventhandler`|Název procedury, která zpracovává událost.|
|||
  
## <a name="remarks"></a>Poznámky  
 Příkazy `AddHandler` a`RemoveHandler` umožňují kdykoli spustit a zastavit zpracování událostí během provádění programu.  
  
 Podpis `eventhandler` procedury se musí shodovat s signaturou události `event`.  
  
 `Handles` Klíčové slovo `AddHandler` a příkaz umožňují určit, že konkrétní procedury budou zpracovávat konkrétní události, ale existují rozdíly. `AddHandler` Příkaz propojuje procedury s událostmi v době běhu. Při definování procedury použijte klíčovéslovo,kteréurčuje,žezpracujekonkrétníudálost.`Handles` Další informace najdete v tématu [obslužné rutiny](../../../visual-basic/language-reference/statements/handles-clause.md).  
  
> [!NOTE]
> Pro vlastní události `AddHandler` Vyvolá příkaz `AddHandler` přístup k události. Další informace o vlastních událostech naleznete v tématu [příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Řeší](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
