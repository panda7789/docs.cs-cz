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
ms.openlocfilehash: 867bf97ea13654de6f9c0209c64b9320824f9665
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931754"
---
# <a name="method-implementation-in-custom-controls"></a>Implementace metody ve vlastních ovládacích prvcích
Metoda je implementována v ovládacím prvku stejným způsobem, jako by byla metoda implementována v jakékoli jiné součásti.  
  
 V Visual Basic, pokud je metoda nutná k vrácení hodnoty, je implementována jako `Public Function`. Pokud není vrácena žádná hodnota, je implementována jako `Public Sub`. Metody jsou deklarovány pomocí následující syntaxe:  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 Vzhledem k tomu, že funkce vrací hodnotu, musí určovat návratový typ, jako je například celé číslo, řetězec, objekt a tak dále. Musí být `Function` zadány i argumenty nebo `Sub` procedury, pokud existují.  
  
 C#nerozlišuje mezi funkcemi a procedurami, jak Visual Basic. Metoda buď vrátí hodnotu, nebo vrátí `void`hodnotu. Syntaxe pro deklaraci C# veřejné metody je:  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 Pokud deklarujete metodu, deklarujte všechny její argumenty jako explicitní datové typy, kdykoli je to možné. Argumenty, které přijímají odkazy na objekty, by měly být deklarovány jako konkrétní `As Widget` typy třídy `As Object`, například namísto. V Visual Basic výchozí nastavení `Option Strict` toto pravidlo automaticky vynutilo.  
  
 Typové argumenty umožňují, aby kompilátor mohl zachytit mnoho chyb vývojářů, nikoli v době běhu. Kompilátor vždycky zachycuje chyby, zatímco testování za běhu je pouze to vhodné jako testovací sada.  
  
## <a name="overloaded-methods"></a>Přetížené metody  
 Chcete-li umožnit uživatelům vašeho ovládacího prvku poskytnout různé kombinace parametrů metodě, poskytněte více přetížení metody pomocí explicitních datových typů. Vyhněte se vytváření `As Object` parametrů deklarovaných, které mohou obsahovat libovolný datový typ, protože to může vést k chybám, které nemusí být zachyceny při testování.  
  
> [!NOTE]
> Univerzální datový typ v modulu CLR (Common Language Runtime `Object` ) je `Variant`spíše než. `Variant`byl odebrán z jazyka.  
  
 Například `Spin` metoda hypotetického `Widget` ovládacího prvku může umožňovat přímé určení směru a rychlosti, nebo specifikace jiného `Widget` objektu, ze kterého má být absorbována potenciál:  
  
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
