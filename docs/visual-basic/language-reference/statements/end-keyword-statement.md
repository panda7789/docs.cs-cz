---
title: End &lt;– klíčové slovo&gt; – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: d65c921a1631cd38c4d0d1ab9b34db3d7e43a97e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654838"
---
# <a name="end-ltkeywordgt-statement-visual-basic"></a>End &lt;– klíčové slovo&gt; – příkaz (Visual Basic)

Pokud následuje další klíčové slovo, ukončí definici bloku příkazů zavedených v dané klíčové slovo.

## <a name="syntax"></a>Syntaxe

```vb
End AddHandler
End Class
End Enum
End Event
End Function
End Get
End If
End Interface
End Module
End Namespace
End Operator
End Property
End RaiseEvent  
End RemoveHandler  
End Select
End Set
End Structure
End Sub
End SyncLock
End Try
End While
End With  
```  
  
## <a name="parts"></a>Součásti

|Část|Popis|
|---|---|
|`End`|Povinný parametr. Ukončí definici programovací element.|
|`AddHandler`|Povinnost ukončit `AddHandler` přistupující objekt zahájené odpovídající `AddHandler` příkaz ve vlastním [Event – příkaz](event-statement.md).|
|`Class`|Povinnost ukončit definici třídy zahájené odpovídající [Class – příkaz](class-statement.md).|
|`Enum`|Povinnost ukončit definice výčtu zahájené odpovídající [Enum – příkaz](enum-statement.md).|
|`Event`|Povinnost ukončit `Custom` definice události zahájené odpovídající [Event – příkaz](event-statement.md).|  
|`Function`|Povinnost ukončit `Function` definici procedury zahájené odpovídající [Function – příkaz](function-statement.md). Pokud se zjistí spuštění `End Function` prohlášení, ovládací prvek vrátí volajícímu kódu.|
|`Get`|Povinnost ukončit `Property` definici procedury zahájené odpovídající [získat příkaz](get-statement.md). Pokud se zjistí spuštění `End Get` prohlášení, ovládací prvek vrátí příkaz požaduje hodnotu vlastnosti.|
|`If`|Povinnost ukončit `If`... `Then`... `Else` blokovat definice zahájené odpovídající `If` příkazu. Zobrazit [Pokud... Potom... Else – příkaz](if-then-else-statement.md).|
|`Interface`|Povinnost ukončit definici rozhraní zahájené odpovídající [Interface – příkaz](interface-statement.md).|
|`Module`|Povinnost ukončit modulu definice zahájené odpovídající [Module – příkaz](module-statement.md).|
|`Namespace`|Povinnost ukončit definice oboru názvů zahájené odpovídající [příkaz Namespace](namespace-statement.md).|
|`Operator`|Povinnost ukončit definici operátoru zahájené odpovídající [Operator – příkaz](operator-statement.md).|
|`Property`|Povinnost ukončit definici vlastnosti zahájené odpovídající [Property – příkaz](property-statement.md).|
|`RaiseEvent`|Povinnost ukončit `RaiseEvent` přistupující objekt zahájené odpovídající `RaiseEvent` příkaz ve vlastním [Event – příkaz](event-statement.md).|
|`RemoveHandler`|Povinnost ukončit `RemoveHandler` přistupující objekt zahájené odpovídající `RemoveHandler` příkaz ve vlastním [Event – příkaz](event-statement.md).|
|`Select`|Povinnost ukončit `Select`... `Case` blokovat definice zahájené odpovídající `Select` příkazu. Zobrazit [vyberte... Case – příkaz](select-case-statement.md).  
|`Set`|Povinnost ukončit `Property` definici procedury zahájené odpovídající [nastavit příkaz](set-statement.md). Pokud se zjistí spuštění `End Set` prohlášení, ovládací prvek vrátí příkaz pro nastavení vlastnosti na hodnotu.  
|`Structure`|Povinnost ukončit definici struktury zahájené odpovídající [Structure – příkaz](structure-statement.md).  
|`Sub`|Povinnost ukončit `Sub` definici procedury zahájené odpovídající [příkaz Sub](sub-statement.md). Pokud se zjistí spuštění `End Sub` prohlášení, ovládací prvek vrátí volajícímu kódu.  
|`SyncLock`|Povinnost ukončit `SyncLock` blokovat definice zahájené odpovídající `SyncLock` příkazu. Zobrazit [příkaz SyncLock](synclock-statement.md).  
|`Try`|Povinnost ukončit `Try`... `Catch`... `Finally` blokovat definice zahájené odpovídající `Try` příkazu. Zobrazit [zkuste... Catch... Příkaz finally](try-catch-finally-statement.md).  
|`While`|Povinnost ukončit `While` smyčky definice zahájené odpovídající `While` příkazu. Zobrazit [během... End While – příkaz](while-end-while-statement.md).  
|`With`| Povinnost ukončit `With` blokovat definice zahájené odpovídající `With` příkazu. Zobrazit [s... End With – příkaz](with-end-with-statement.md).  
|||
  
## <a name="directives"></a>Direktivy

Když uvozená znakem čísla (`#`), `End` – klíčové slovo ukončí blok předzpracování zavedených v direktivě odpovídající.  

```vb
#End ExternalSource
#End If
#End Region
```

|Část|Popis|
|---|---|
|`#End`|Povinný parametr. Ukončí definici bloku předběžného zpracování.|
|`ExternalSource`|Povinnost ukončit z externího zdroje bloku zahájené odpovídající [#ExternalSource – direktiva](../directives/externalsource-directive.md).|
|`If`|Povinnost ukončit blok podmíněné kompilace zahájené odpovídající `#If` směrnice. Zobrazit [#If... Then... #Else – direktivy](../directives/if-then-else-directives.md).|
|`Region`|Povinnost ukončit blok zdrojové oblasti zahájené odpovídající [#Region – direktiva](../directives/region-directive.md).|
|||

## <a name="remarks"></a>Poznámky

[End – příkaz](end-statement.md), bez dodatečné klíčové slovo ukončí provádění okamžitě.

## <a name="smart-device-developer-notes"></a>Poznámky pro vývojáře inteligentního zařízení  

`End` Příkaz bez další klíčové slovo, není podporován.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz End](end-statement.md)
