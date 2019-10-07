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
ms.openlocfilehash: 95277f532488b0cf56114e5ee94dc3528e3a2e02
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004541"
---
# <a name="addhandler-statement"></a>AddHandler – příkaz
Přidruží událost k obslužné rutině události v době běhu.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Součásti  
|||
|---|---|
|event|Název události, která má být zpracována.|  
|`eventhandler`|Název procedury, která zpracovává událost.|
|||
  
## <a name="remarks"></a>Poznámky  
 Příkazy `AddHandler` a `RemoveHandler` umožňují spuštění a zastavení zpracování událostí kdykoli během provádění programu.  
  
 Signatura procedury `eventhandler` se musí shodovat s signaturou události `event`.  
  
 Klíčové slovo `Handles` a příkaz `AddHandler` umožňují určit, že konkrétní procedury budou zpracovávat konkrétní události, ale existují rozdíly. Příkaz `AddHandler` spojuje procedury s událostmi v době běhu. Při definování procedury použijte klíčové slovo `Handles`, které určuje, že zpracuje konkrétní událost. Další informace najdete v tématu [obslužné rutiny](../../../visual-basic/language-reference/statements/handles-clause.md).  
  
> [!NOTE]
> Pro vlastní události příkaz `AddHandler` vyvolá přistupující objekt `AddHandler` události. Další informace o vlastních událostech naleznete v tématu [příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Řeší](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
