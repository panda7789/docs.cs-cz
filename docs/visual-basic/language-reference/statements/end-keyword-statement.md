---
title: "End &lt;– klíčové slovo&gt; – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cf0ac1221f8a85a8a43599d9c5ec210884205e5e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="end-ltkeywordgt-statement-visual-basic"></a>End &lt;– klíčové slovo&gt; – příkaz (Visual Basic)
Když následuje další klíčové slovo, ukončí definici bloku příkaz zavedených v tomto – klíčové slovo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 `End`  
 Požadováno. Ukončí definici programovací element.  
  
 `AddHandler`  
 Požadovaný pro ukončení `AddHandler` přistupujícího objektu spuštěno pomocí odpovídající `AddHandler` příkaz v vlastní [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `Class`  
 Požadovaný pro ukončení definice třídy spuštěno pomocí odpovídající [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md).  
  
 `Enum`  
 Požadovaný pro ukončení definice výčtu spuštěno pomocí odpovídající [Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
 `Event`  
 Požadovaný pro ukončení `Custom` událostí definice spuštěno pomocí odpovídající [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `Function`  
 Požadovaný pro ukončení `Function` definice procedury spuštěno pomocí odpovídající [funkce příkaz](../../../visual-basic/language-reference/statements/function-statement.md). Pokud provádění dojde `End``Function` ovládací prvek příkaz vrátí kód volání.  
  
 `Get`  
 Požadovaný pro ukončení `Property` definice procedury spuštěno pomocí odpovídající [získat příkaz](../../../visual-basic/language-reference/statements/get-statement.md). Pokud provádění dojde `End``Get` ovládací prvek prohlášení, vrátí příkaz žádají o hodnotu vlastnosti.  
  
 `If`  
 Požadovaný pro ukončení `If`... `Then`... `Else` blokovat definice spuštěno pomocí odpovídající `If` příkaz. V tématu [Pokud... Potom... Else – příkaz](../../../visual-basic/language-reference/statements/if-then-else-statement.md).  
  
 `Interface`  
 Požadovaný pro ukončení definice rozhraní spuštěno pomocí odpovídající [Interface – příkaz](../../../visual-basic/language-reference/statements/interface-statement.md).  
  
 `Module`  
 Požadovaný pro ukončení definice modulu spuštěno pomocí odpovídající [Module – příkaz](../../../visual-basic/language-reference/statements/module-statement.md).  
  
 `Namespace`  
 Požadovaný pro ukončení definici oboru názvů spuštěno pomocí odpovídající [příkaz Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md).  
  
 `Operator`  
 Požadovaný pro ukončení definici operátor spuštěno pomocí odpovídající [Operator – příkaz](../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 `Property`  
 Požadovaný pro ukončení definice vlastnosti spuštěno pomocí odpovídající [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md).  
  
 `RaiseEvent`  
 Požadovaný pro ukončení `RaiseEvent` přistupujícího objektu spuštěno pomocí odpovídající `RaiseEvent` příkaz v vlastní [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `RemoveHandler`  
 Požadovaný pro ukončení `RemoveHandler` přistupujícího objektu spuštěno pomocí odpovídající `RemoveHandler` příkaz v vlastní [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `Select`  
 Požadovaný pro ukončení `Select`... `Case` blokovat definice spuštěno pomocí odpovídající `Select` příkaz. V tématu [vyberte... Příkaz případ](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
 `Set`  
 Požadovaný pro ukončení `Property` definice procedury spuštěno pomocí odpovídající [příkaz Set](../../../visual-basic/language-reference/statements/set-statement.md). Pokud provádění dojde `End``Set` ovládací prvek příkaz, vrátí příkaz Nastavení hodnoty vlastnosti.  
  
 `Structure`  
 Požadovaný pro ukončení definice struktury spuštěno pomocí odpovídající [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md).  
  
 `Sub`  
 Požadovaný pro ukončení `Sub` definice procedury spuštěno pomocí odpovídající [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md). Pokud provádění dojde `End``Sub` ovládací prvek příkaz vrátí kód volání.  
  
 `SyncLock`  
 Požadovaný pro ukončení `SyncLock` blokovat definice spuštěno pomocí odpovídající `SyncLock` příkaz. V tématu [SyncLock – příkaz](../../../visual-basic/language-reference/statements/synclock-statement.md).  
  
 `Try`  
 Požadovaný pro ukončení `Try`... `Catch`... `Finally` blokovat definice spuštěno pomocí odpovídající `Try` příkaz. V tématu [zkuste... Catch... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 `While`  
 Požadovaný pro ukončení `While` cykly definice spuštěno pomocí odpovídající `While` příkaz. V tématu [při... End While – příkaz](../../../visual-basic/language-reference/statements/while-end-while-statement.md).  
  
 `With`  
 Požadovaný pro ukončení `With` blokovat definice spuštěno pomocí odpovídající `With` příkaz. V tématu [s... End With – příkaz](../../../visual-basic/language-reference/statements/with-end-with-statement.md).  
  
## <a name="remarks"></a>Poznámky  
 [End – příkaz](../../../visual-basic/language-reference/statements/end-statement.md), bez další klíčového slova, ukončí provádění okamžitě.  
  
 Když uvozená znakem čísla (`#`), `End` – klíčové slovo ukončí blok předběžného zpracování zaváděné odpovídající direktivu.  
  
 `#End`  
 Požadováno. Ukončí definici předběžného zpracování bloku.  
  
 `#ExternalSource`  
 Požadovaný pro ukončení bloku externí zdroj, který je spuštěno pomocí odpovídající [#ExternalSource – direktiva](../../../visual-basic/language-reference/directives/externalsource-directive.md).  
  
 `#If`  
 Požadovaný pro ukončení blok Podmíněná kompilace spuštěno pomocí odpovídající `#If` – direktiva. V tématu [#If... Then... #Else – direktivy](../../../visual-basic/language-reference/directives/if-then-else-directives.md).  
  
 `#Region`  
 Požadovaný pro ukončení blok oblast zdroj spuštěno pomocí odpovídající [#Region – direktiva](../../../visual-basic/language-reference/directives/region-directive.md).  
  
## <a name="smart-device-developer-notes"></a>Poznámky pro vývojáře inteligentního zařízení  
 `End` Příkaz bez další klíčového slova, není podporován.  
  
## <a name="see-also"></a>Viz také  
 [End – příkaz](../../../visual-basic/language-reference/statements/end-statement.md)
