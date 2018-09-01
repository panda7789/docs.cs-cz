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
ms.openlocfilehash: f731ff150bd901e325726fca5aa682ff1770f979
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396484"
---
# <a name="addhandler-statement"></a>AddHandler – příkaz
Přidruží událost k obslužné rutiny události v době běhu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Součásti  
|||
|---|---|
|event|Název události ke zpracování.|  
|`eventhandler`|Název procedury, která zpracovává událost.|
|||
  
## <a name="remarks"></a>Poznámky  
 `AddHandler` a `RemoveHandler` příkazy umožňují spustit a zastavit zpracování událostí v průběhu provádění programu.  
  
 Podpis metody `eventhandler` postupu musí odpovídat signatuře události `event`.  
  
 `Handles` – Klíčové slovo a `AddHandler` příkaz oba umožňují určit, že konkrétní postupy zpracování určité události, ale existují rozdíly. `AddHandler` Příkaz se připojí postupy k událostem v době běhu. Použití `Handles` – klíčové slovo při definování proceduru k určení, že zpracovává konkrétní události. Další informace najdete v tématu [zpracovává](../../../visual-basic/language-reference/statements/handles-clause.md).  
  
> [!NOTE]
>  Pro vlastní události `AddHandler` příkaz volá události `AddHandler` přistupujícího objektu. Další informace o vlastních událostech najdete v tématu [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Příkaz RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [Obslužné rutiny](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
