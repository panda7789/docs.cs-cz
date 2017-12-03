---
title: Vlastnosti vs. Arguments
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14651389-4a49-4cbb-9ddf-c83fdc155df1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4fcb38322d6b068095238add9334aa2d081c4a5d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="properties-vs-arguments"></a>Vlastnosti vs. Arguments
Existuje několik možností pro předávání dat na aktivity. Kromě používání <xref:System.Activities.InArgument>, aktivity lze také vytvořit které přijímat data pomocí standardní vlastnosti CLR nebo veřejné <xref:System.Activities.ActivityAction> vlastnosti. Toto téma popisuje, jak chcete vybrat typ odpovídající metodu.  
  
## <a name="using-clr-properties"></a>Pomocí vlastnosti CLR  
 Při předávání dat do aktivity, jsou vlastnosti CLR (to znamená, veřejné metody, použijte získání a nastavení rutiny vystavit data) možnost, která má nejvíce omezení. Hodnota parametru předána do vlastnosti CLR musí být známo při kompilaci řešení; Tato hodnota bude stejný pro všechny instance pracovního postupu. Tímto způsobem je podobná konstanta definované v kódu; hodnota předaná do vlastnosti CLR Tuto hodnotu nelze změnit po dobu trvání aktivity a pro různé instance aktivity nelze změnit. <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A>Příklad vlastnosti CLR vystavené aktivitu; Název metody, která volá aktivita nelze změnit na základě podmínky runtime a budou stejné pro všechny instance aktivity.  
  
## <a name="using-arguments"></a>Pomocí argumenty  
 Argumenty by měl být použit při vyhodnocení dat pouze jednou po dobu životnosti aktivity; To znamená jeho hodnota se nezmění po dobu životnosti aktivity, ale hodnota mohou být různé pro různé instance aktivity. <xref:System.Activities.Statements.If.Condition%2A>Příklad hodnoty, který získá vyhodnotit jednou; Proto je definován jako argument. <xref:System.Activities.Statements.WriteLine.Text%2A>je další příklad metodu, která by měl být definován jako argument, protože je Vyhodnocená jenom jednou během provádění aktivity, ale může lišit pro různé instance aktivity.  
  
## <a name="using-activityaction"></a>Pomocí ActivityAction  
 Když dat je potřeba zhodnotit vícekrát po dobu životnosti provádění aktivity <xref:System.Activities.ActivityAction> by měl být použit. Například <xref:System.Activities.Statements.While.Condition%2A> vlastnost je vyhodnotit pro každou iteraci <xref:System.Activities.Statements.While> smyčky. Pokud <xref:System.Activities.InArgument> měla použít pro tento účel, že opakování ve smyčce by nikdy konec, protože argument nebude znovu vyhodnocena pro každou iteraci a by vždy vrátit stejný výsledek.
