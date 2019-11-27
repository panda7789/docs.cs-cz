---
title: End <keyword> – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 87f4724cc036e6e0bdf0b558854a4034f45b9ab5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343737"
---
# <a name="end-keyword-statement-visual-basic"></a>End \<– klíčové slovo > příkaz (Visual Basic)

Po následování klíčového slova další se ukončí definice bloku příkazu, který je představený tímto klíčovým slovem.

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

|Částí|Popis|
|---|---|
|`End`|Požadováno. Ukončí definici programovacího prvku.|
|`AddHandler`|Vyžadovaná k ukončení přístupového objektu `AddHandler` začal pomocí odpovídajícího příkazu `AddHandler` ve vlastním [příkazu události](event-statement.md).|
|`Class`|Požadováno pro ukončení definice třídy zahájené párovým [příkazem třídy](class-statement.md).|
|`Enum`|Požadováno pro ukončení definice výčtu zahájené párovým [příkazem výčtu](enum-statement.md).|
|`Event`|Vyžadovaná pro ukončení definice události `Custom` zahájená párovým [příkazem události](event-statement.md).|  
|`Function`|Požadováno pro ukončení definice `Function` procedury zahájené párovým [příkazem funkce](function-statement.md). Pokud spuštění narazí na příkaz `End Function`, ovládací prvek se vrátí volajícímu kódu.|
|`Get`|Vyžadovaná k ukončení definice `Property` procedury, kterou začaly párovým [příkazem Get](get-statement.md). Pokud spuštění narazí na příkaz `End Get`, ovládací prvek se vrátí do příkazu, který požaduje hodnotu vlastnosti.|
|`If`|Vyžadovaná k ukončení `If`...`Then`...`Else` definice bloku začala pomocí odpovídajícího `If`ho příkazu. Zjistit [, zda... Pak... ELSE – příkaz](if-then-else-statement.md).|
|`Interface`|Požadováno pro ukončení definice rozhraní, kterou začaly pomocí odpovídajícího [příkazu rozhraní](interface-statement.md).|
|`Module`|Vyžadovaná k ukončení definice modulu zahájené párovým [příkazem modulu](module-statement.md).|
|`Namespace`|Požadováno pro ukončení definice oboru názvů zahájené párovým [příkazem Namespace](namespace-statement.md).|
|`Operator`|Požadováno pro ukončení definice operátora zahájena párovým [příkazem operátoru](operator-statement.md).|
|`Property`|Požadováno pro ukončení definice vlastnosti zahájené v rámci odpovídajícího [příkazu vlastnosti](property-statement.md).|
|`RaiseEvent`|Vyžadovaná k ukončení přístupového objektu `RaiseEvent` začal pomocí odpovídajícího příkazu `RaiseEvent` ve vlastním [příkazu události](event-statement.md).|
|`RemoveHandler`|Vyžadovaná k ukončení přístupového objektu `RemoveHandler` začal pomocí odpovídajícího příkazu `RemoveHandler` ve vlastním [příkazu události](event-statement.md).|
|`Select`|Vyžadovaná k ukončení `Select`...`Case` definice bloku začala pomocí odpovídajícího příkazu `Select`. Viz [Vybrat... Příkaz Case](select-case-statement.md).  
|`Set`|Požadováno pro ukončení definice `Property` procedury, kterou začaly pomocí odpovídajícího [příkazu set](set-statement.md). Pokud spuštění narazí na příkaz `End Set`, vrátí se ovládací prvek do příkazu, který nastaví hodnotu vlastnosti.  
|`Structure`|Požadováno pro ukončení definice struktury zahájené [příkazem odpovídajícího struktury](structure-statement.md).  
|`Sub`|Požadováno pro ukončení definice `Sub` procedury zahájené párovým [příkazem Sub sub](sub-statement.md). Pokud spuštění narazí na příkaz `End Sub`, ovládací prvek se vrátí volajícímu kódu.  
|`SyncLock`|Požadováno pro ukončení definice `SyncLock` bloku zahájené párovým příkazem `SyncLock`. Viz [příkaz SyncLock](synclock-statement.md).  
|`Try`|Požadavek na ukončení `Try`...`Catch`...`Finally` definice bloku začala párovým příkazem `Try`. Viz [Try... Zachytit... Finally – příkaz](try-catch-finally-statement.md).  
|`While`|Vyžadovaná k ukončení definice `While` smyčky začala pomocí odpovídajícího příkazu `While`. Viz [while... Příkaz End While](while-end-while-statement.md).  
|`With`| Požadováno pro ukončení definice `With` bloku zahájené párovým příkazem `With`. Viz [s... Příkaz end with](with-end-with-statement.md)  
|||
  
## <a name="directives"></a>Direktivy

Pokud předchází znaménko čísla (`#`), klíčové slovo `End` ukončí blok předzpracování, který zavedla odpovídající direktiva.  

```vb
#End ExternalSource
#End If
#End Region
```

|Částí|Popis|
|---|---|
|`#End`|Požadováno. Ukončí definici bloku předzpracování.|
|`ExternalSource`|Požadováno pro ukončení externího bloku zdroje zahájeného pomocí vyhovující [direktivy #ExternalSource](../directives/externalsource-directive.md).|
|`If`|Požadováno pro ukončení podmíněného kompilačního bloku zahájeného pomocí vyhovující direktivy `#If`. Viz [#If... Then... #Else direktivy](../directives/if-then-else-directives.md).|
|`Region`|Požadováno pro ukončení bloku zdrojové oblasti, který začal odpovídat [direktivě #Region](../directives/region-directive.md).|
|||

## <a name="remarks"></a>Poznámky

[Příkaz end](end-statement.md)bez dalšího klíčového slova ukončí provádění okamžitě.

## <a name="smart-device-developer-notes"></a>Poznámky pro vývojáře inteligentního zařízení  

Příkaz `End` bez dalšího klíčového slova není podporován.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz End](end-statement.md)
