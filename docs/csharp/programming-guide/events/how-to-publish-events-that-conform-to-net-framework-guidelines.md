---
title: "Postupy: Publikování událostí odpovídajících směrnicím rozhraní .NET Framework (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 570729e432146b4ef97e4c487f644b12b354bb4a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a><span data-ttu-id="60259-102">Postupy: Publikování událostí odpovídajících směrnicím rozhraní .NET Framework (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="60259-102">How to: Publish Events that Conform to .NET Framework Guidelines (C# Programming Guide)</span></span>
<span data-ttu-id="60259-103">Následující postup ukazuje, jak přidat události, které následují standardní [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] vzor třídy a struktury.</span><span class="sxs-lookup"><span data-stu-id="60259-103">The following procedure demonstrates how to add events that follow the standard [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pattern to your classes and structs.</span></span> <span data-ttu-id="60259-104">Všechny události v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] jsou na základě knihovny tříd <xref:System.EventHandler> delegáta, který je definován následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="60259-104">All events in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
>  <span data-ttu-id="60259-105">[!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] Představuje obecné verzi tohoto delegáta <xref:System.EventHandler%601>.</span><span class="sxs-lookup"><span data-stu-id="60259-105">The [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="60259-106">Následující příklady ukazují, jak používat obě verze.</span><span class="sxs-lookup"><span data-stu-id="60259-106">The following examples show how to use both versions.</span></span>  
  
 <span data-ttu-id="60259-107">I když událostí v třídách, které definujete, může být založené na libovolného typu platný delegáta, i delegáti, které vrací hodnotu, se obecně doporučuje založit události na [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] vzor pomocí <xref:System.EventHandler>, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="60259-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="60259-108">Chcete-li publikovat události na základě vzoru obslužná rutina události</span><span class="sxs-lookup"><span data-stu-id="60259-108">To publish events based on the EventHandler pattern</span></span>  
  
1.  <span data-ttu-id="60259-109">(Tento krok přeskočte a přejděte na krok 3a, pokud nemáte odeslat vlastní data s vaší událostí.) Deklarování třídy pro vaše vlastní data v oboru, který je viditelná pro třídy vydavatele a odběratele.</span><span class="sxs-lookup"><span data-stu-id="60259-109">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="60259-110">Pak přidejte požadované členy pro uložení dat vlastních událostí.</span><span class="sxs-lookup"><span data-stu-id="60259-110">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="60259-111">V tomto příkladu se vrátí jednoduchým řetězcem.</span><span class="sxs-lookup"><span data-stu-id="60259-111">In this example, a simple string is returned.</span></span>  
  
    ```csharp  
    public class CustomEventArgs : EventArgs  
    {  
        public CustomEventArgs(string s)  
        {  
            msg = s;  
        }  
        private string msg;  
        public string Message  
        {  
            get { return msg; }  
        }   
    }  
    ```  
  
2.  <span data-ttu-id="60259-112">(Tento krok přeskočte, pokud používáte obecný verzi <xref:System.EventHandler%601> .) Ve třídě publikování delegáta deklarujte.</span><span class="sxs-lookup"><span data-stu-id="60259-112">(Skip this step if you are using the generic version of <xref:System.EventHandler%601> .) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="60259-113">Zadejte jeho název, který končí *obslužná rutina události*.</span><span class="sxs-lookup"><span data-stu-id="60259-113">Give it a name that ends with *EventHandler*.</span></span> <span data-ttu-id="60259-114">Druhý parametr určuje vaše vlastní typ EventArgs.</span><span class="sxs-lookup"><span data-stu-id="60259-114">The second parameter specifies your custom EventArgs type.</span></span>  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3.  <span data-ttu-id="60259-115">Deklarace událostí v třídě publikování pomocí jedné z následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="60259-115">Declare the event in your publishing class by using one of the following steps.</span></span>  
  
    1.  <span data-ttu-id="60259-116">Pokud máte žádné vlastní třídy EventArgs, bude váš typ události delegát neobecnou obslužná rutina události.</span><span class="sxs-lookup"><span data-stu-id="60259-116">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="60259-117">Nemáte delegáta deklarovat, protože je již deklarována <xref:System> obor názvů, který je součástí při vytváření projektu C#.</span><span class="sxs-lookup"><span data-stu-id="60259-117">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="60259-118">Přidejte následující kód do vaší třídy vydavatele.</span><span class="sxs-lookup"><span data-stu-id="60259-118">Add the following code to your publisher class.</span></span>  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2.  <span data-ttu-id="60259-119">Pokud používáte verzi neobecnou <xref:System.EventHandler> a máte vlastní třídy odvozené od <xref:System.EventArgs>, deklarování událost v třídě publikování a použití delegáta z kroku 2 jako typ.</span><span class="sxs-lookup"><span data-stu-id="60259-119">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3.  <span data-ttu-id="60259-120">Pokud používáte obecný verze, není nutné vlastní delegáta.</span><span class="sxs-lookup"><span data-stu-id="60259-120">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="60259-121">Místo toho v třídě publikování zadat typ vašeho událostí jako `EventHandler<CustomEventArgs>`, nahraďte název vlastní třídy mezi lomené závorky.</span><span class="sxs-lookup"><span data-stu-id="60259-121">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a><span data-ttu-id="60259-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="60259-122">Example</span></span>  
 <span data-ttu-id="60259-123">Následující příklad ukazuje předchozí kroky, pomocí vlastní třídy EventArgs a <xref:System.EventHandler%601> jako typ události.</span><span class="sxs-lookup"><span data-stu-id="60259-123">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>  
  
 [!code-csharp[csProgGuideEvents#2](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-publish-events-that-conform-to-net-framework-guidelines_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="60259-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="60259-124">See Also</span></span>  
 <xref:System.Delegate>  
 [<span data-ttu-id="60259-125">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="60259-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="60259-126">Události</span><span class="sxs-lookup"><span data-stu-id="60259-126">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="60259-127">Delegáti</span><span class="sxs-lookup"><span data-stu-id="60259-127">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
