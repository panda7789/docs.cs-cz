---
title: Implementace metody ve vlastních ovládacích prvcích
ms.date: 03/30/2017
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
ms.openlocfilehash: 38dcad25af31b87afc1cc6ef4f89a1f7903bc0ed
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117414"
---
# <a name="method-implementation-in-custom-controls"></a>Implementace metody ve vlastních ovládacích prvcích
Metoda je implementována v ovládacím prvku stejným způsobem, který by implementovat metodu v jiné součásti.  
  
 V jazyce Visual Basic, pokud je potřeba metoda vrátí hodnotu, je implementován jako `Public Function`. Pokud není vrácena žádná hodnota, je implementovaný jako `Public Sub`. Metody jsou deklarovány pomocí následující syntaxe:  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 Protože funkce vrátí hodnotu, se musí zadat návratovým typem, jako je například integer, string, objektu a tak dále. Argumenty `Function` nebo `Sub` využít postupy, pokud existuje, musí být také zadána.  
  
 C#nerozlišuje mezi funkcemi a postupy, stejně jako jazyka Visual Basic. Metoda vrací hodnotu, nebo vrátí `void`. Syntaxe pro deklarování C# veřejnou metodu je:  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 Při deklaraci metody deklarujte všechny argumenty jako explicitní datové typy, kdykoli je to možné. Argumenty, které trvat odkazy na objekty by měly být deklarovány jako typy určité třídy – například `As Widget` místo `As Object`. V jazyce Visual Basic, výchozí nastavení `Option Strict` automaticky vynutí toto pravidlo.  
  
 Typové argumenty umožňují zachytit kompilátorem, spíše než v době běhu mnoho chyb pro vývojáře. Kompilátor vždy zachytí chyby, zatímco za běhu testování je jenom tak dobré jako sadu testů.  
  
## <a name="overloaded-methods"></a>Přetížené metody  
 Pokud chcete povolit uživatelům ovládacího prvku k poskytování různých kombinací parametry pro metodu, poskytují několik přetížení metody, pomocí explicitní datových typů. Vyhněte se vytváření parametry deklarovanými jako `As Object` , který může obsahovat žádný datový typ, jako to může vést k chybám, které nemusí být zachycena v testování.  
  
> [!NOTE]
>  Univerzální datový typ v modulu common language runtime je `Object` spíše než `Variant`. `Variant` byl odebrán z jazyka.  
  
 Například `Spin` metoda hypotetické `Widget` ovládací prvek může umožnit přímý specifikace typu číselník směru a rychlost nebo specifikace jiného `Widget` má být odebíraný objekt, ze které podpora angular:  
  
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
  
## <a name="see-also"></a>Viz také:

- [Události](../../../standard/events/index.md)
- [Vlastnosti v ovládacích prvcích Windows Forms](properties-in-windows-forms-controls.md)
