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
# <a name="method-implementation-in-custom-controls"></a><span data-ttu-id="1c439-102">Implementace metody ve vlastních ovládacích prvcích</span><span class="sxs-lookup"><span data-stu-id="1c439-102">Method Implementation in Custom Controls</span></span>
<span data-ttu-id="1c439-103">Metoda je implementována v ovládacím prvku stejným způsobem, jako by byla metoda implementována v jakékoli jiné součásti.</span><span class="sxs-lookup"><span data-stu-id="1c439-103">A method is implemented in a control in the same manner a method would be implemented in any other component.</span></span>  
  
 <span data-ttu-id="1c439-104">V Visual Basic, pokud je metoda nutná k vrácení hodnoty, je implementována jako `Public Function`.</span><span class="sxs-lookup"><span data-stu-id="1c439-104">In Visual Basic, if a method is required to return a value, it is implemented as a `Public Function`.</span></span> <span data-ttu-id="1c439-105">Pokud není vrácena žádná hodnota, je implementována jako `Public Sub`.</span><span class="sxs-lookup"><span data-stu-id="1c439-105">If no value is returned, it is implemented as a `Public Sub`.</span></span> <span data-ttu-id="1c439-106">Metody jsou deklarovány pomocí následující syntaxe:</span><span class="sxs-lookup"><span data-stu-id="1c439-106">Methods are declared using the following syntax:</span></span>  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 <span data-ttu-id="1c439-107">Vzhledem k tomu, že funkce vrací hodnotu, musí určovat návratový typ, jako je například celé číslo, řetězec, objekt a tak dále.</span><span class="sxs-lookup"><span data-stu-id="1c439-107">Because functions return a value, they must specify a return type, such as integer, string, object, and so on.</span></span> <span data-ttu-id="1c439-108">Musí být `Function` zadány i argumenty nebo `Sub` procedury, pokud existují.</span><span class="sxs-lookup"><span data-stu-id="1c439-108">The arguments `Function` or `Sub` procedures take, if any, must also be specified.</span></span>  
  
 <span data-ttu-id="1c439-109">C#nerozlišuje mezi funkcemi a procedurami, jak Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1c439-109">C# makes no distinction between functions and procedures, as Visual Basic does.</span></span> <span data-ttu-id="1c439-110">Metoda buď vrátí hodnotu, nebo vrátí `void`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1c439-110">A method either returns a value or returns `void`.</span></span> <span data-ttu-id="1c439-111">Syntaxe pro deklaraci C# veřejné metody je:</span><span class="sxs-lookup"><span data-stu-id="1c439-111">The syntax for declaring a C# public method is:</span></span>  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 <span data-ttu-id="1c439-112">Pokud deklarujete metodu, deklarujte všechny její argumenty jako explicitní datové typy, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="1c439-112">When you declare a method, declare all of its arguments as explicit data types whenever possible.</span></span> <span data-ttu-id="1c439-113">Argumenty, které přijímají odkazy na objekty, by měly být deklarovány jako konkrétní `As Widget` typy třídy `As Object`, například namísto.</span><span class="sxs-lookup"><span data-stu-id="1c439-113">Arguments that take object references should be declared as specific class types — for example, `As Widget` instead of `As Object`.</span></span> <span data-ttu-id="1c439-114">V Visual Basic výchozí nastavení `Option Strict` toto pravidlo automaticky vynutilo.</span><span class="sxs-lookup"><span data-stu-id="1c439-114">In Visual Basic, the default setting `Option Strict` automatically enforces this rule.</span></span>  
  
 <span data-ttu-id="1c439-115">Typové argumenty umožňují, aby kompilátor mohl zachytit mnoho chyb vývojářů, nikoli v době běhu.</span><span class="sxs-lookup"><span data-stu-id="1c439-115">Typed arguments allow many developer errors to be caught by the compiler, rather than at run time.</span></span> <span data-ttu-id="1c439-116">Kompilátor vždycky zachycuje chyby, zatímco testování za běhu je pouze to vhodné jako testovací sada.</span><span class="sxs-lookup"><span data-stu-id="1c439-116">The compiler always catches errors, whereas run-time testing is only as good as the test suite.</span></span>  
  
## <a name="overloaded-methods"></a><span data-ttu-id="1c439-117">Přetížené metody</span><span class="sxs-lookup"><span data-stu-id="1c439-117">Overloaded Methods</span></span>  
 <span data-ttu-id="1c439-118">Chcete-li umožnit uživatelům vašeho ovládacího prvku poskytnout různé kombinace parametrů metodě, poskytněte více přetížení metody pomocí explicitních datových typů.</span><span class="sxs-lookup"><span data-stu-id="1c439-118">If you want to allow users of your control to supply different combinations of parameters to a method, provide multiple overloads of the method, using explicit data types.</span></span> <span data-ttu-id="1c439-119">Vyhněte se vytváření `As Object` parametrů deklarovaných, které mohou obsahovat libovolný datový typ, protože to může vést k chybám, které nemusí být zachyceny při testování.</span><span class="sxs-lookup"><span data-stu-id="1c439-119">Avoid creating parameters declared `As Object` that can contain any data type, as this can lead to errors that might not be caught in testing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c439-120">Univerzální datový typ v modulu CLR (Common Language Runtime `Object` ) je `Variant`spíše než.</span><span class="sxs-lookup"><span data-stu-id="1c439-120">The universal data type in the common language runtime is `Object` rather than `Variant`.</span></span> <span data-ttu-id="1c439-121">`Variant`byl odebrán z jazyka.</span><span class="sxs-lookup"><span data-stu-id="1c439-121">`Variant` has been removed from the language.</span></span>  
  
 <span data-ttu-id="1c439-122">Například `Spin` metoda hypotetického `Widget` ovládacího prvku může umožňovat přímé určení směru a rychlosti, nebo specifikace jiného `Widget` objektu, ze kterého má být absorbována potenciál:</span><span class="sxs-lookup"><span data-stu-id="1c439-122">For example, the `Spin` method of a hypothetical `Widget` control might allow either direct specification of spin direction and speed, or specification of another `Widget` object from which angular momentum is to be absorbed:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1c439-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c439-123">See also</span></span>

- [<span data-ttu-id="1c439-124">Události</span><span class="sxs-lookup"><span data-stu-id="1c439-124">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="1c439-125">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1c439-125">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
