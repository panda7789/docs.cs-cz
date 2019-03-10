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
ms.openlocfilehash: 5bcc6441ab1a615c31a5a028fc7f8f09cbdd4c10
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710365"
---
# <a name="method-implementation-in-custom-controls"></a><span data-ttu-id="b3f08-102">Implementace metody ve vlastních ovládacích prvcích</span><span class="sxs-lookup"><span data-stu-id="b3f08-102">Method Implementation in Custom Controls</span></span>
<span data-ttu-id="b3f08-103">Metoda je implementována v ovládacím prvku stejným způsobem, který by implementovat metodu v jiné součásti.</span><span class="sxs-lookup"><span data-stu-id="b3f08-103">A method is implemented in a control in the same manner a method would be implemented in any other component.</span></span>  
  
 <span data-ttu-id="b3f08-104">V jazyce Visual Basic, pokud je potřeba metoda vrátí hodnotu, je implementován jako `Public Function`.</span><span class="sxs-lookup"><span data-stu-id="b3f08-104">In Visual Basic, if a method is required to return a value, it is implemented as a `Public Function`.</span></span> <span data-ttu-id="b3f08-105">Pokud není vrácena žádná hodnota, je implementovaný jako `Public Sub`.</span><span class="sxs-lookup"><span data-stu-id="b3f08-105">If no value is returned, it is implemented as a `Public Sub`.</span></span> <span data-ttu-id="b3f08-106">Metody jsou deklarovány pomocí následující syntaxe:</span><span class="sxs-lookup"><span data-stu-id="b3f08-106">Methods are declared using the following syntax:</span></span>  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 <span data-ttu-id="b3f08-107">Protože funkce vrátí hodnotu, se musí zadat návratovým typem, jako je například integer, string, objektu a tak dále.</span><span class="sxs-lookup"><span data-stu-id="b3f08-107">Because functions return a value, they must specify a return type, such as integer, string, object, and so on.</span></span> <span data-ttu-id="b3f08-108">Argumenty `Function` nebo `Sub` využít postupy, pokud existuje, musí být také zadána.</span><span class="sxs-lookup"><span data-stu-id="b3f08-108">The arguments `Function` or `Sub` procedures take, if any, must also be specified.</span></span>  
  
 <span data-ttu-id="b3f08-109">C#nerozlišuje mezi funkcemi a postupy, stejně jako jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b3f08-109">C# makes no distinction between functions and procedures, as Visual Basic does.</span></span> <span data-ttu-id="b3f08-110">Metoda vrací hodnotu, nebo vrátí `void`.</span><span class="sxs-lookup"><span data-stu-id="b3f08-110">A method either returns a value or returns `void`.</span></span> <span data-ttu-id="b3f08-111">Syntaxe pro deklarování C# veřejnou metodu je:</span><span class="sxs-lookup"><span data-stu-id="b3f08-111">The syntax for declaring a C# public method is:</span></span>  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 <span data-ttu-id="b3f08-112">Při deklaraci metody deklarujte všechny argumenty jako explicitní datové typy, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="b3f08-112">When you declare a method, declare all of its arguments as explicit data types whenever possible.</span></span> <span data-ttu-id="b3f08-113">Argumenty, které trvat odkazy na objekty by měly být deklarovány jako typy určité třídy – například `As Widget` místo `As Object`.</span><span class="sxs-lookup"><span data-stu-id="b3f08-113">Arguments that take object references should be declared as specific class types — for example, `As Widget` instead of `As Object`.</span></span> <span data-ttu-id="b3f08-114">V jazyce Visual Basic, výchozí nastavení `Option Strict` automaticky vynutí toto pravidlo.</span><span class="sxs-lookup"><span data-stu-id="b3f08-114">In Visual Basic, the default setting `Option Strict` automatically enforces this rule.</span></span>  
  
 <span data-ttu-id="b3f08-115">Typové argumenty umožňují zachytit kompilátorem, spíše než v době běhu mnoho chyb pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="b3f08-115">Typed arguments allow many developer errors to be caught by the compiler, rather than at run time.</span></span> <span data-ttu-id="b3f08-116">Kompilátor vždy zachytí chyby, zatímco za běhu testování je jenom tak dobré jako sadu testů.</span><span class="sxs-lookup"><span data-stu-id="b3f08-116">The compiler always catches errors, whereas run-time testing is only as good as the test suite.</span></span>  
  
## <a name="overloaded-methods"></a><span data-ttu-id="b3f08-117">Přetížené metody</span><span class="sxs-lookup"><span data-stu-id="b3f08-117">Overloaded Methods</span></span>  
 <span data-ttu-id="b3f08-118">Pokud chcete povolit uživatelům ovládacího prvku k poskytování různých kombinací parametry pro metodu, poskytují několik přetížení metody, pomocí explicitní datových typů.</span><span class="sxs-lookup"><span data-stu-id="b3f08-118">If you want to allow users of your control to supply different combinations of parameters to a method, provide multiple overloads of the method, using explicit data types.</span></span> <span data-ttu-id="b3f08-119">Vyhněte se vytváření parametry deklarovanými jako `As Object` , který může obsahovat žádný datový typ, jako to může vést k chybám, které nemusí být zachycena v testování.</span><span class="sxs-lookup"><span data-stu-id="b3f08-119">Avoid creating parameters declared `As Object` that can contain any data type, as this can lead to errors that might not be caught in testing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3f08-120">Univerzální datový typ v modulu common language runtime je `Object` spíše než `Variant`.</span><span class="sxs-lookup"><span data-stu-id="b3f08-120">The universal data type in the common language runtime is `Object` rather than `Variant`.</span></span> <span data-ttu-id="b3f08-121">`Variant` byl odebrán z jazyka.</span><span class="sxs-lookup"><span data-stu-id="b3f08-121">`Variant` has been removed from the language.</span></span>  
  
 <span data-ttu-id="b3f08-122">Například `Spin` metoda hypotetické `Widget` ovládací prvek může umožnit přímý specifikace typu číselník směru a rychlost nebo specifikace jiného `Widget` má být odebíraný objekt, ze které podpora angular:</span><span class="sxs-lookup"><span data-stu-id="b3f08-122">For example, the `Spin` method of a hypothetical `Widget` control might allow either direct specification of spin direction and speed, or specification of another `Widget` object from which angular momentum is to be absorbed:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b3f08-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3f08-123">See also</span></span>
- [<span data-ttu-id="b3f08-124">Události</span><span class="sxs-lookup"><span data-stu-id="b3f08-124">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="b3f08-125">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b3f08-125">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
