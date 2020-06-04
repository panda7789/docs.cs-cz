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
ms.openlocfilehash: de995a13b34678410e2af74b59f2d0c467982b75
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408481"
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
 `AddHandler`Příkazy a `RemoveHandler` umožňují kdykoli spustit a zastavit zpracování událostí během provádění programu.  
  
 Podpis `eventhandler` procedury se musí shodovat s signaturou události `event` .  
  
 `Handles`Klíčové slovo a `AddHandler` příkaz umožňují určit, že konkrétní procedury budou zpracovávat konkrétní události, ale existují rozdíly. `AddHandler`Příkaz propojuje procedury s událostmi v době běhu. `Handles`Při definování procedury použijte klíčové slovo, které určuje, že zpracuje konkrétní událost. Další informace najdete v tématu [obslužné rutiny](handles-clause.md).  
  
> [!NOTE]
> Pro vlastní události `AddHandler` Vyvolá příkaz přístup k události `AddHandler` . Další informace o vlastních událostech naleznete v tématu [příkaz Event](event-statement.md).  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Viz také

- [RemoveHandler – příkaz](removehandler-statement.md)
- [Handles](handles-clause.md)
- [Event – příkaz](event-statement.md)
- [Události](../../programming-guide/language-features/events/index.md)
