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
# <a name="method-implementation-in-custom-controls"></a><span data-ttu-id="f3a66-102">Implementace metody ve vlastních ovládacích prvcích</span><span class="sxs-lookup"><span data-stu-id="f3a66-102">Method Implementation in Custom Controls</span></span>
<span data-ttu-id="f3a66-103">Metoda je implementována v ovládacím prvku stejným způsobem, který ve jakoukoli jinou součástí by být implementována metoda.</span><span class="sxs-lookup"><span data-stu-id="f3a66-103">A method is implemented in a control in the same manner a method would be implemented in any other component.</span></span>  
  
 <span data-ttu-id="f3a66-104">V jazyce Visual Basic, pokud je metoda je nutný k vrácení hodnoty, jsou implementované jako `Public Function`.</span><span class="sxs-lookup"><span data-stu-id="f3a66-104">In Visual Basic, if a method is required to return a value, it is implemented as a `Public Function`.</span></span> <span data-ttu-id="f3a66-105">Pokud je vrácena žádná hodnota, je implementovaný jako `Public Sub`.</span><span class="sxs-lookup"><span data-stu-id="f3a66-105">If no value is returned, it is implemented as a `Public Sub`.</span></span> <span data-ttu-id="f3a66-106">Metody jsou deklarovány pomocí následující syntaxe:</span><span class="sxs-lookup"><span data-stu-id="f3a66-106">Methods are declared using the following syntax:</span></span>  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 <span data-ttu-id="f3a66-107">Protože funkce vrátí hodnotu, musí zadat návratový typ, například celé číslo, řetězec, objekt a tak dále.</span><span class="sxs-lookup"><span data-stu-id="f3a66-107">Because functions return a value, they must specify a return type, such as integer, string, object, and so on.</span></span> <span data-ttu-id="f3a66-108">Argumenty `Function` nebo `Sub` postupy využít, pokud existuje, musí být také zadána.</span><span class="sxs-lookup"><span data-stu-id="f3a66-108">The arguments `Function` or `Sub` procedures take, if any, must also be specified.</span></span>  
  
 <span data-ttu-id="f3a66-109">C# nerozlišuje mezi funkcemi a postupy, jak to dělá jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f3a66-109">C# makes no distinction between functions and procedures, as Visual Basic does.</span></span> <span data-ttu-id="f3a66-110">Metoda vrátí hodnotu, nebo vrátí `void`.</span><span class="sxs-lookup"><span data-stu-id="f3a66-110">A method either returns a value or returns `void`.</span></span> <span data-ttu-id="f3a66-111">Tady je syntax deklarace veřejnou metodu C#:</span><span class="sxs-lookup"><span data-stu-id="f3a66-111">The syntax for declaring a C# public method is:</span></span>  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 <span data-ttu-id="f3a66-112">Po deklarování metodu deklarujte všechny argumenty jako explicitní datové typy, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="f3a66-112">When you declare a method, declare all of its arguments as explicit data types whenever possible.</span></span> <span data-ttu-id="f3a66-113">Argumenty, které trvat odkazy na objekty musí být deklarována jako typy určité třídy – například `As Widget` místo `As Object`.</span><span class="sxs-lookup"><span data-stu-id="f3a66-113">Arguments that take object references should be declared as specific class types — for example, `As Widget` instead of `As Object`.</span></span> <span data-ttu-id="f3a66-114">V jazyce Visual Basic, výchozí nastavení `Option Strict` automaticky vynucuje toto pravidlo.</span><span class="sxs-lookup"><span data-stu-id="f3a66-114">In Visual Basic, the default setting `Option Strict` automatically enforces this rule.</span></span>  
  
 <span data-ttu-id="f3a66-115">Argumenty typu povolit mnoho chyb vývojáře k zachycení, kompilátorem spíše než v době běhu.</span><span class="sxs-lookup"><span data-stu-id="f3a66-115">Typed arguments allow many developer errors to be caught by the compiler, rather than at run time.</span></span> <span data-ttu-id="f3a66-116">Kompilátor vždy zachytí chyby, zatímco spuštění testování je pouze jako vhodný jako testovací sadu.</span><span class="sxs-lookup"><span data-stu-id="f3a66-116">The compiler always catches errors, whereas run-time testing is only as good as the test suite.</span></span>  
  
## <a name="overloaded-methods"></a><span data-ttu-id="f3a66-117">Přetížené metody</span><span class="sxs-lookup"><span data-stu-id="f3a66-117">Overloaded Methods</span></span>  
 <span data-ttu-id="f3a66-118">Pokud chcete povolit uživatelům vlastního ovládacího prvku zadat různé kombinace parametrů na metodu, zadejte více přetížení metody, pomocí explicitní datových typů.</span><span class="sxs-lookup"><span data-stu-id="f3a66-118">If you want to allow users of your control to supply different combinations of parameters to a method, provide multiple overloads of the method, using explicit data types.</span></span> <span data-ttu-id="f3a66-119">Vyhněte se vytváření parametry deklarovaný `As Object` , může obsahovat libovolný typ dat, jako to může způsobit chyby, které nemusí být zachyceny v testování.</span><span class="sxs-lookup"><span data-stu-id="f3a66-119">Avoid creating parameters declared `As Object` that can contain any data type, as this can lead to errors that might not be caught in testing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3a66-120">Je univerzální datového typu ve modul common language runtime `Object` místo `Variant`.</span><span class="sxs-lookup"><span data-stu-id="f3a66-120">The universal data type in the common language runtime is `Object` rather than `Variant`.</span></span> <span data-ttu-id="f3a66-121">`Variant`byla odebrána od jazyka.</span><span class="sxs-lookup"><span data-stu-id="f3a66-121">`Variant` has been removed from the language.</span></span>  
  
 <span data-ttu-id="f3a66-122">Například `Spin` metodu hypotetický `Widget` řízení může povolit buď přímé specifikaci typu číselník směr a rychlost, nebo specifikace jiného `Widget` objekt z které úhlová informací má být odebíraný:</span><span class="sxs-lookup"><span data-stu-id="f3a66-122">For example, the `Spin` method of a hypothetical `Widget` control might allow either direct specification of spin direction and speed, or specification of another `Widget` object from which angular momentum is to be absorbed:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f3a66-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3a66-123">See Also</span></span>  
 [<span data-ttu-id="f3a66-124">Události</span><span class="sxs-lookup"><span data-stu-id="f3a66-124">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="f3a66-125">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3a66-125">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
