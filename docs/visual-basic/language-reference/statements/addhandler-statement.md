---
title: AddHandler – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: db8131dc82aed40e725c9375efef274fb6917d41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603649"
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
 [Příkaz RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [Obslužné rutiny](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
