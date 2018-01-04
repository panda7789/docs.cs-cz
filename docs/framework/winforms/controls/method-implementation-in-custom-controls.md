---
title: "Implementace metody ve vlastních ovládacích prvcích"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], method implementation
- custom controls [Windows Forms], overloading methods
- custom controls [Windows Forms], method implementation
- methods [Windows Forms]
- methods [Windows Forms], custom controls
ms.assetid: 35d14fca-4bb4-4a27-8211-1f7a98ea27de
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e07d4a5f0a4e66e412b22e1f6cabd24cd81b5ea4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="method-implementation-in-custom-controls"></a>Implementace metody ve vlastních ovládacích prvcích
Metoda je implementována v ovládacím prvku stejným způsobem, který ve jakoukoli jinou součástí by být implementována metoda.  
  
 V jazyce Visual Basic, pokud je metoda je nutný k vrácení hodnoty, jsou implementované jako `Public Function`. Pokud je vrácena žádná hodnota, je implementovaný jako `Public Sub`. Metody jsou deklarovány pomocí následující syntaxe:  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 Protože funkce vrátí hodnotu, musí zadat návratový typ, například celé číslo, řetězec, objekt a tak dále. Argumenty `Function` nebo `Sub` postupy využít, pokud existuje, musí být také zadána.  
  
 C# nerozlišuje mezi funkcemi a postupy, jak to dělá jazyka Visual Basic. Metoda vrátí hodnotu, nebo vrátí `void`. Tady je syntax deklarace veřejnou metodu C#:  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 Po deklarování metodu deklarujte všechny argumenty jako explicitní datové typy, kdykoli je to možné. Argumenty, které trvat odkazy na objekty musí být deklarována jako typy určité třídy – například `As Widget` místo `As Object`. V jazyce Visual Basic, výchozí nastavení `Option Strict` automaticky vynucuje toto pravidlo.  
  
 Argumenty typu povolit mnoho chyb vývojáře k zachycení, kompilátorem spíše než v době běhu. Kompilátor vždy zachytí chyby, zatímco spuštění testování je pouze jako vhodný jako testovací sadu.  
  
## <a name="overloaded-methods"></a>Přetížené metody  
 Pokud chcete povolit uživatelům vlastního ovládacího prvku zadat různé kombinace parametrů na metodu, zadejte více přetížení metody, pomocí explicitní datových typů. Vyhněte se vytváření parametry deklarovaný `As Object` , může obsahovat libovolný typ dat, jako to může způsobit chyby, které nemusí být zachyceny v testování.  
  
> [!NOTE]
>  Je univerzální datového typu ve modul common language runtime `Object` místo `Variant`. `Variant`byla odebrána od jazyka.  
  
 Například `Spin` metodu hypotetický `Widget` řízení může povolit buď přímé specifikaci typu číselník směr a rychlost, nebo specifikace jiného `Widget` objekt z které úhlová informací má být odebíraný:  
  
```vb  
Overloads Public Sub Spin( _  
   ByVal SpinDirection As SpinDirectionsEnum, _  
   ByVal RevolutionsPerSecond As Double)  
   ' Implementation code here.  
End Sub  
Overloads Public Sub Spin(ByVal Driver As Widget) _  
   ' Implementation code here.  
End Sub  
```  
  
```csharp  
public void Spin(SpinDirectionsEnum spinDirection, double revolutionsPerSecond)  
{  
   // Implementation code here.  
}  
  
public void Spin(Widget driver)  
{  
   // Implementation code here.  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Události](../../../../docs/standard/events/index.md)  
 [Vlastnosti v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
