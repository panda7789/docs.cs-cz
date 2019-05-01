---
title: Vlastnosti versus Arguments
ms.date: 03/30/2017
ms.assetid: 14651389-4a49-4cbb-9ddf-c83fdc155df1
ms.openlocfilehash: a6ea4755599f18e8bbaa8187941623578d2168ac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962627"
---
# <a name="properties-vs-arguments"></a>Vlastnosti versus Arguments
Nejsou k dispozici pro předávání dat do aktivity několik možností. Kromě použití <xref:System.Activities.InArgument>, aktivity mohou také být vytvořeny, které přijímají data pomocí standardní vlastnosti CLR nebo veřejné <xref:System.Activities.ActivityAction> vlastnosti. Toto téma popisuje, jak vybrat typ odpovídající metodu.  
  
## <a name="using-clr-properties"></a>Pomocí vlastnosti CLR  
 Při předávání dat do aktivity, jsou vlastnosti CLR (to znamená, veřejné metody, použijte Get i Set rutiny ke zveřejňování dat) na možnost, která má nejvíce omezení. Hodnota parametru předaná do vlastnosti CLR musí být známo při kompilaci řešení; Tato hodnota bude stejná pro všechny instance pracovního postupu. Tímto způsobem je podobný konstanta definovaná v kódu; hodnotu předanou do vlastnosti CLR Tuto hodnotu nelze změnit po celou dobu životnosti aktivity a pro různé instance aktivity nelze změnit. <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A> je příkladem vlastnost CLR vystavené aktivitu; Název metody, která volá aktivity nelze měnit v závislosti na podmínkám modulu runtime a budou stejné pro všechny instance aktivity.  
  
## <a name="using-arguments"></a>Pomocí argumentů  
 Použití argumentů při dat je vyhodnocen pouze jednou během životního cyklu aktivit; To znamená jeho hodnota se nezmění po celou dobu životnosti aktivity, ale hodnota se může lišit pro různé instance aktivity. <xref:System.Activities.Statements.If.Condition%2A> Následuje příklad hodnotu, která získá vyhodnotí jednou; Proto je definován jako argument. <xref:System.Activities.Statements.WriteLine.Text%2A> je další příklad metodu, která musí být definován jako argument, protože je vyhodnocen pouze jednou během provádění aktivity, ale může lišit pro různé instance aktivity.  
  
## <a name="using-activityaction"></a>Pomocí ActivityAction  
 Když data je potřeba zhodnotit vícekrát během životního cyklu spuštění aktivity <xref:System.Activities.ActivityAction> by měla sloužit. Například <xref:System.Activities.Statements.While.Condition%2A> vlastnost je vyhodnocen pro každou iteraci <xref:System.Activities.Statements.While> smyčky. Pokud <xref:System.Activities.InArgument> byly použity pro tento účel, smyčky nikdy ukončit, protože argument by se znovu vyhodnotit pro každou iteraci a by vždy vrátí stejné výsledky.
